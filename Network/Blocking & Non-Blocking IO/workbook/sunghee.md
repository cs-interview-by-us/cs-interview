### ****Q1. blocking I/O와 non blocking I/O의 차이점을 호출 시 코드의 실행 흐름을 중심으로 설명해주세요.****

**Blocking I/O**

<img src="https://user-images.githubusercontent.com/31344894/201096834-1a7cbc9b-99d8-4fda-9646-5207cea8b37e.png">

   - 어플리케이션의 스레드에서 코드가 실행되다가 read() system call을 Blocking모드로 호출하면 해당 스레드는 block됨
- system call로 인해 kernel모드로 전환돼 read I/O를 실행시킴(관련있는 디바이스에 요청)
- 디바이스에서 준비됐다고 응답을 주면 커널이 그 응답을 받고 준비가 된 데이터를 커널space에서 유저space로 옮기게 됨
- 블락이 됐던 스레드가 깨어나 준비가 된 데이터를 읽고 이어서 코드를 실행함

**Non Blocking I/O**

<img src="https://user-images.githubusercontent.com/31344894/201096732-20a3c5c2-ee35-4aac-a606-8c69d4c7c6e4.png">

- 어플리케이션의 스레드에서 코드가 실행되다가 read() system call을 Non-Blocking모드로 호출하면 kernel로 context switch되고 read I/O를 실행시킴 + 바로 리턴 시킴(Linux 기준 -1과 에러코드(EAGAIN or EWOULDBLOCK))
- 스레드는 block되지 않고 이어서 다른 코드를 실행할 수 있음
- 실행하는 동안 I/O 디바이스로부터 읽을 준비가 됐다는 응답이 커널로 와 커널이 데이터를 준비해놓음
- 어플리케이션(스레드)은 다른 작업들을 수행하다가 중간에 read() system call을 Non-Blocking모드로 호출해  kernel로 context switch하면 데이터가 준비돼있는 상태이기 때문에 커널이 스레드로 요청했던 데이터를 전송함
- 스레드에서 데이터를 읽고 이어서 코드를 실행함

### ****Q2. non-blocking과 asynchronous의 차이점을 설명해주세요.****

- non-blocking : 제어권이 넘겨 지지 않으므로, 대상의 작업 처리 여부와 상관이 없이 호출한 함수
 측에서 제어권을 가지고 다음 작업들을 수행할 수 있음

- Asynchronous : 호출한 함수는 호출된 함수의 결과를 기다리지만, 제어권이 어떻게 될지는 관심이 없음. 비동기적으로 다른 함수가 실행이 된다는 데에 의미가 있고 호출된 함수의 결과값을 받게 되는데 다른 비동기 함수로 부터 받은 결과값에 대해 모든 순서가 완전히 보장이 될 수는 없다는 의미.

Non-blocking은 제어권의 관점, Asynchronous은 시간의 관점으로 봐야함

[Blocking, Non-blocking & Synchronous, Asynchronous](https://programming119.tistory.com/238)