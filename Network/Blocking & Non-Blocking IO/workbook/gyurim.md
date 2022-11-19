# Blocking & Non-Blocking I/O

### Q1. blocking I/O와 non blocking I/O의 차이점을 호출 시 코드의 실행 흐름을 중심으로 설명해주세요. 

- non-blocking I/O
    <img width="500" alt="nonblocking" src="https://user-images.githubusercontent.com/31344894/201096732-20a3c5c2-ee35-4aac-a606-8c69d4c7c6e4.png">
    - read I/O를 하기 위해 system call을 수행하면 커널의 I/O 작업 완료 여부와는 무관하게 즉시 응답합니다. 
    - 이는 커널이 시스템 콜을 받자마자 CPU 제어권을 다시 어플리케이션에게 넘겨주고, 따라서 어플리케이션은 I/O 작업이 완료되기 전에 다른 작업을 수행할 수 있습니다. 

- blocking I/O
    <img width="500" alt="Blocking" src="https://user-images.githubusercontent.com/31344894/201096834-1a7cbc9b-99d8-4fda-9646-5207cea8b37e.png">
    - 어플리케이션에서 Read()를 호출해 커널에 read I/O를 요청하면, read가 끝날 때까지 어플리케이션은 block되어 다른 작업을 하지 못합니다. 

### Q2. non-blocking과 asynchronous의 차이점을 설명해주세요. 
> Non-Blocking은 호출된 함수가 자신의 작업이 종료되지 않아도 제어권을 호출한 함수에게 넘겨줘 호출한 함수가 작업을 할 수 있도록 해줍니다. 
> 
> Asynchronous는 호출한 함수는 해당 작업의 결과 값을 상관하지 않고, 호출된 함수가 콜백으로 결과 값을 넘겨주는 방식 등으로 결과 처리를 하는 것입니다. 
>
> Non-Blocking은 제어의 관점, Asynchronous는 작업 완료 여부를 신경쓰는 유무의 관점으로 봐야합니다. 