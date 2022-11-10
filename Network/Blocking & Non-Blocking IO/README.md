# Blocking & Non-Blocking I/O

## I/O
- I/O란 데이터의 입력(input)과 출력(output)을 함께 일컫는 말입니다. 
- 디바이스를 통해 입력과 출력이 이뤄지는 작업
- 예시
    - 파일 I/O
    - 네트워크를 통해서 다른 서버로 데이터를 전송
    - 다른 서버로부터 데이터를 전송받는 것
    - 콘솔에 출력하는 것 (스트림을 통해 출력하기 때문에 I/O)


## Blocking I/O
### Blocking
- 자신의 작업을 진행하다가 다른 주체의 작업이 시작되면 다른 작업이 끝날 때까지 **기다렸다**가 자신의 작업을 시작하는 것
- 호출된 함수가 자신의 작업을 모두 마칠 때까지 호출한 함수에게 제어권을 넘겨주지 않고 대기하게 만드는 것 

<img width="294" alt="cpu blocking" src="https://user-images.githubusercontent.com/31344894/201104668-b395d6ec-af25-45b4-b86a-e6a91440d956.png">

### Blocking I/O
- I/O 작업이 진행되는 동안 유저 프로세스가 자신의 작업을 중단한 채, I/O가 끝날 때까지 대기하는 방식 

<img width="581" alt="Blocking" src="https://user-images.githubusercontent.com/31344894/201096834-1a7cbc9b-99d8-4fda-9646-5207cea8b37e.png">

- 어플리케이션은 ```Read()```를 호출해 커널에 read I/O를 요청하면, read가 끝날 때까지 application은 block되어 다른 작업을 하지 못합니다.
- read I/O가 수행 완료될 때까지는 어플리케이션이 다른 작업을 수행하지 못한다는 것을 의미합니다. 

## Non-Blocking I/O
### Non-Blocking
- 다른 주체의 작업에 **관련없이** 자신의 작업을 하는 것 
- 호출된 함수가 바로 리턴해서 호출한 함수에게 제어권을 넘겨주고, 호출한 함수가 다른 일을 할 수 있는 기회를 주는 것 

<img width="292" alt="cpu non blocking" src="https://user-images.githubusercontent.com/31344894/201104659-a3547bb2-2354-40bf-bc8b-a3de0e4a12eb.png">

### Non-Blocking I/O
- 한 함수가 I/O 작업을 호출했을 때, I/O 작업이 완료될 때까지 해당 함수의 작업을 중단하지 않고 I/O 호출에 대해 즉시 리턴하고 함수가 이어서 다른 일을 수행할 수 있도록 하는 방식 

<img width="601" alt="nonblocking" src="https://user-images.githubusercontent.com/31344894/201096732-20a3c5c2-ee35-4aac-a606-8c69d4c7c6e4.png">

> EWOULDBLOCK: 데이터가 없다는 메세지 

- read I/O를 하기 위해 system call을 수행하면, 커널의 I/O 작업 완료 여부와는 무관하게 즉시 응답합니다. 
- 이는 커널이 시스템 콜을 받자마자 CPU 제어권을 다시 어플리케이션에게 넘겨주고, 따라서 어플리케이션은 I/O 작업이 완료되기 전에 다른 작업을 수행할 수 있습니다. 
- 어플리케이션은 다른 작업들을 수행하다가 중간 중간에 시스템 콜을 보내서 I/O가 완료되었는지 커널에게 물어보고, 완료되면 I/O 작업을 완료합니다. 


## 참고
- https://etloveguitar.tistory.com/140 ✨
- https://baek-kim-dev.site/38
- https://didu-story.tistory.com/307