# String, StringBuilder, StringBuffer 차이

> Java에서 문자열을 다루는 대표적인 클래스로 String, StringBuffer, StringBuilder가 있습니다.
> 
> **연산횟수가 많아지거나 멀티스레드, Race condition 등의 상황이 자주 발생**한다면!
> 
> 각 클래스의 특징을 이해하고 상황에 맞는 적절한 클래스를 사용해줘야합니다. 

## String VS StringBuilder, StringBuffer

- String과 StringBuilder, StringBuffer의 **가장 큰 차이점은 ✨String은 불변(immutable)** 이라는 것입니다. 
- 반대로, **✨StringBuffer/StringBuilder 클래스는 가변성**을 가지기 때문에 .append(), .delete() 등 API를 이용하여 **동일 객체 내에서 문자열을 변경하는 것이 가능**합니다. 

### String 클래스와 Heap 메모리 부족 

```Java
String str = "hello"; 
str = str + "world";
```
- 위 예시는 String 참조변수 str이 가리키는 곳에 저장된 "hello"에 "world" 문자열을 더해 "hello world"로 **변경된 것이 아닙니다**. 

<img width="476" alt="string" src="https://user-images.githubusercontent.com/31344894/202722602-944f13fe-ae74-4dea-aa19-391ba496488b.png">

- str 변수는 "hello world" 값을 가지고 있는 새로운 메모리 영역을 가리키게 변경됩니다.
- "hello" 값이 할당되어 있는 메모리 영역은 **Garbage로 남아있다가 GC(garbage collection)에 의해 사라지게 됩니다.**
- ✨String 클래스는 불변하기 때문에 문자열을 수정하는 시점에 새로운 String 인스턴스가 생성된 것입니다. 

- String 클래스는 언제 사용하면 좋을까❓
    - 변하지 않는 문자열을 자주 읽어들이는 경우 String을 사용하면 좋은 성능을 기대할 수 있습니다.
    - 반면 문자열 추가, 수정, 삭제 등의 연산이 빈번하게 발생하는 알고리즘에 String 클래스를 사용하면 **힙 메모리(Heap)에 많은 임시 가비지(Garbage)가 생성되어 힙 메모리 부족**으로 어플리케이션 성능에 치명적인 영향을 끼치게 됩니다. 

- 문자열 추가, 수정, 삭제 등의 연산이 빈번하게 발생할 땐 어떤 클래스를 사용하면 좋을까❓ 
    - String 대신 StringBuffer, StringBuilder를 사용하면 됩니다. 
    <img width="476" alt="stringbuffer" src="https://user-images.githubusercontent.com/31344894/202724051-6b2eaf38-3c40-4057-bb06-44f052559398.png">


## StringBuilder vs StringBuffer
- StringBuilder와 StringBuffer의 **가장 큰 차이점은 동기화의 유무**입니다. 
- **✨StringBuffer는 동기화 키워드를 지원**하여 멀티스레드 환경에서 thread-safe합니다. 
- 참고로 String도 불변성을 가지기 때문에 멀티스레드 환경에서 thread-safe합니다. 
- **✨StringBuilder는 동기화를 지원하지 않기** 때문에 멀티스레드 환경에서 사용하는 것은 적합하지 않으나, **단일스레드에서 성능은 StringBuffer보다 뛰어납니다.**

## 클래스 별 특징 정리❗️
- String: 문자열 연산이 적고 멀티스레드 환경일 경우
- StringBuffer: 문자열 연산이 많고 멀티스레드 환경일 경우
- StringBuilder: 문자열 연산이 많고 단일 스레드이거나 동기화를 고려하지 않아도 되는 경우 

<img width="476" alt="string class" src="https://user-images.githubusercontent.com/31344894/202725001-0963bb7e-19be-4b80-88ee-1b9b3fb2ff2b.png">


### 참고
- https://ifuwanna.tistory.com/221