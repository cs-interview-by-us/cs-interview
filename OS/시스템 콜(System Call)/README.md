# System Call

운영체제 : 커널 모드(Kernel Mode)와 사용자 모드(User Mode)로 나뉘어 구동됨

**시스템 콜 :** 커널 영역의 기능을 사용자 모드가 사용 가능하게,  
__즉 프로세스가 하드웨어에 직접 접근해서 필요한 기능을 사용할 수 있게 해줌__

---

시스템 콜의 유형은 6가지(프로세스 제어, 파일 조작, 장치 조작, 정보 유지보수, 통신, 보호)로 나뉘는데,   
그 중 **프로세스 제어** 중 3가지(fork, exec, wait)만 실습해보자

- fork, exec : 새로운 Process 생성과 관련
- wait : Process (Parent)가 만든 다른 Process(child) 가 끝날 때까지 기다리는 명령어

---

### fork

새로운 Process를 생성할 때 사용  
But, 이상한 방식

```cpp
#include <iostream>
#include <unistd.h> //Unix에서 사용하는 c컴파일러 헤더파일 (fork, getpid 사용)
using namespace std;

int main() {
    cout << "pid :" << (int) getpid() << "\n"; // pid : 29146

    int rc = fork();                    // 주목 !!

    if (rc < 0) {
        exit(1);
    }                                      // (1) fork 실패
    else if (rc == 0) {                    // (2) child 인 경우(fork 값이 0)
        cout << "child (pid : " << (int) getpid() << ")\n";
    } else {                                // (3) parent인 경우(fork 값이 1 이상)
        cout << "parent of " << rc << "(pid : " << (int) getpid() << ")\n";
    }
}
```

> pid : 29146
> 
> 
> parent of 29147 (pid : 29146)
> 
> child (pid : 29147)
> 

을 출력함 (parent와 child 순서는 non-deterministic함(비결정론적) 

→ 즉 확신 X, scheduler가 결정하는 일)

> pid : 29146
> 
> 
> child (pid : 29147)
> 
> parent of 29147 (pid : 29146)
> 

이와 같이 출력될 수도 있다는 것

````aside
💡 해석  
pid : 프로세스 식별자, Unix 시스템에서 pid는 프로세스에게 명령할 때 사용함

1. fork()실행되는 순간 프로세스가 하나 더 생기는데, 이 때 생긴 프로세스(child)는 fork를 만든 프로세스(parent)와 *거의 동일한 복사본을 갖게됨
2. 이 때 OS는 '위와 똑같은 2개의 프로그램이 동작한다고 생각하고, fork()가 return될 차례'라고 생각함  
이 때문에 새로 생성된 process(child)는 main에서 시작하지 않고 if문부터 시작하게 됨

*BUT 차이점 존재. child와 parent의 fork()값이 다르다는 점. So, 완전히 동일한 복사본이라 할 수 없음
- parent fork() 값 : child의 pid 값(1 이상)
- child의 fork() 값 : 0
(parent와 child의 fork 값이 다르다는 점은 매우 유용한 방식 ~)
````

---

### wait

child 프로세스가 종료될 때까지 기다리는 작업

```cpp
#include <iostream>
#include <unistd.h>
using namespace std;

int main() {
    cout << "pid :" << (int) getpid() << "\n";

    int rc = fork();

    if (rc < 0) {
        exit(1);
    }
    else if (rc == 0) { //child
        cout << "child (pid : " << (int) getpid() << ")\n";
    } else { //parent 
        int wc = wait(nullptr);            // 추가된 부분 !!
        cout << "parent of " << rc << "(wc : " << wc << " / pid : " << (int) getpid() << ")\n";
    }
}
```

> pid : 29146
> 
> 
> child (pid : 29147)
> 
> parent of 29147 (wc : 29147 / pid : 29146)
> 

wait를 통해서, child의 실행이 끝날 때까지 기다려줌

parent가 먼저 실행되더라도, wait()는 child가 끝나기 전에는 return하지 않으므로, __반드시 child가 먼저 실행됨__

---

### exec

단순 fork는 동일한 프로세스의 내용을 여러번 동작할 때 사용함

__child에서는 parent와 다른 동작을 하고 싶을 때__ 는 exec를 사용할 수 있음

```cpp
#include <iostream>
#include <unistd.h>
using namespace std;

int main() {
    cout << "pid :" << (int) getpid() << "\n";

    int rc = fork();

    if (rc < 0) {
        exit(1);
    }
    else if (rc == 0) {
        cout << "child (pid : " << (int) getpid() << ")\n";
        char *myargs[3];
        myargs[0] = strdup("wc");     // 내가 실행할 파일 이름
        myargs[1] = strdup("p3.c");       // 실행할 파일에 넘겨줄 argument
        myargs[2] = nullptr;            // end of array
        execvp(myargs[0], myargs);    // wc 파일 실행
        cout << "this shouldn't print out"; // 실행되지 않음
    } else {
        int wc = wait(nullptr);
        cout << "parent of " << rc << "(wc : " << wc << " / pid : " << (int) getpid() << ")\n";
    }
}
```

> pid :8029  
child (pid : 8032)  
parent of 8032(wc : 8032 / pid : 8029)  
<span style="color:red">wc: p3.c: open: No such file or directory (파일 못찾은 거, 찾으면 실행됨)</span>
> 

exec가 실행되면,

execvp(실행파일, 전달인자) 함수는 code segment 영역에 실행 파일의 코드를 읽어와서 덮어 씌움

씌운 이후에는 heap, stack, 다른 메모리 영역이 초기화 되고 OS는 그냥 실행함

즉, __새로운 Process를 생성하지 않고, 현재 프로그램에 wc라는 파일을 실행__ 함

그로 인해서, execvp() 이후의 부분은 실행되지 않음 !  
