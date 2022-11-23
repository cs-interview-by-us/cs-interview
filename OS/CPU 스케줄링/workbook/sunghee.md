### ****Q1. CPU 스케줄링이 필요한 이유****

**CPU 이용율을 최대화**하기 위해서이다. 만약 하나의 프로세스가 CPU를 점유하여 실행(CPU Burst)하다가 특정 I/O처리를 기다려야 한다면, 이 프로세스는 Device Queue에 머무르게 되고 I/O처리를 하는 시간(I/O Burst)동안 CPU는 쉬게 될 것이다. 이는 CPU 이용율을 떨어뜨리게 된다. 따라서 적절한 스케쥴링 방법을 사용하여 CPU Burst Time을 최대로 하는 것이 스케쥴링의 목적이다.

### ****Q2. CPU 스케줄링이 발생하는 상황****

1. 프로세스가 Running 상태에서 Waiting 상태로 전환될 때 (ex. I/O 발생)
2. 프로세스가 Running 상태에서 Ready 상태로 전환될 때 (ex. 인터럽트 발생)
3. 프로세스가 Waiting 상태에서 Ready 상태로 전환될 때 (ex. I/O 종료)
4. 프로세스가 종료할 때

![Untitled](https://user-images.githubusercontent.com/22094204/203258343-d2ad7167-0c84-4c58-91f3-cb2685609085.png)

### ****Q3. SJF와 SRT의 차이****

|  | SJF(Shortest Job First) | SRT(Shortest Remaining Time) |
| --- | --- | --- |
| 방식 | Ready Queue에 있는 프로세스들 중 가장 작은 실행시간을 가진 프로세스가 종료 시까지 CPU 할당받음 | 현재 CPU에서 실행 중인 프로세스의 수행 시간보다 더 짧은 수행 시간을 가진다고 판단되는 프로세스가 Ready Queue에 생기면 언제라도 프로세스가 선점됨 |
| 기법 | 비선점 | 선점 |