# CPU 스케줄링
## CPU 스케줄링이란?
- 다중 프로세서 운영체제에서 CPU 이용률을 최대화하며 프로세스 작업을 수행하기 위해서 다음에 어떤 프로세스를 처리할지(CPU에 어떤 프로세스를 배정할지)를 결정하는 운영체제 커널의 모듈  
즉, CPU 이용률을 최대화 하기 위해서는 좋은 스케줄링 알고리즘이 필요  

> __CPU Scheduler__
실행 준비가 되어 있는 메모리 내의 프로세스(Ready Queue에 있는 프로세스) 중에서 특정한 우선순위를 기반으로 CPU를 할당받을 프로세스를 결정하는 역할

> __Dispatcher__
CPU를 할당할 때, CPU 스케줄러가 선택한 프로세스에 실제로 CPU 코어의 제어를 할당하는 모듈

## CPU 스케줄링 발생 상황
|프로세스 상태|예시|방식|
|---|---|---|
|Running → Waiting|I/O 발생|비선점|
|Running → Reday|인터럽트 발생|선점|
|Waiting → Ready|I/O 완료|선점|
|Terminate|프로세스 종료|비선점|

## CPU 스케줄링 Criteria(성능 척도)
- ```CPU Utilization```: CPU가 쉬고 있지 않게 해야 함
- ```Throughput```: 단위 시간 당 처리량
- ```Turnaround Time```: 수행을 요청한 후 작업이 끝날 때까지 걸린 시간
- ```Waiting Time```: 수행을 요청한 후 작업이 시작될 때까지 걸린 시간
- ```Response Time```: 요청한 후 응답이 올 때까지 걸린 시간

> 일반적으로 ```CPU Utilization```, ```Throughput``` ↑ & ```Turnaround```/```Waiting```/```Response``` Time ↓일 때 성능 good:)

## 선점형(Preemptive) 스케줄링
- 프로세스가 CPU를 할당받아 실행 중이더라도 운영체제가 강제로 CPU를 빼앗을 수 있는 방식

### 장점
- CPU 처리 시간이 매우 긴 프로세스가 CPU 사용 독점을 막을 수 있어 효율적인 운영이 가능
- 높은 우선순위를 가진 프로세스를 빠르게 처리하는 시스템에 유용
- 빠른 응답시간을 요구하는 시분할 시스템에 유용

### 단점
- 높은 우선 순위를 가진 프로세스들만 들어오는 경우 잦은 Context Switching이 일어나 overhead가 많이 발생

### 종류
#### 1. SRT(Shortest Remaining Time)
![](https://velog.velcdn.com/images/imeyh/post/e8b0ce23-5d69-4be9-8ee5-b1abbfdd5143/image.png)
- 가장 짧은 수행 시간을 가진 프로세스를 먼저 수행
- 현재 CPU에서 실행 중인 프로세스의 수행 시간보다 더 짧은 수행 시간을 가진다고 판단되는 프로세스가 Ready Queue에 생기면 언제라도 프로세스가 선점됨

#### 2. RR(Round Robin)
![](https://velog.velcdn.com/images/imeyh/post/8d4fc25e-5a2c-4124-b3bd-b04c650a20d4/image.png)
- 시분할 시스템의 성질을 활용한 방법
- 프로세스마다 같은 ```Time Quantum```(CPU 할당 시간)을 할당하여 프로세스가 할당된 시간 내에 처리 완료를 못하면 Ready Queue의 가장 뒤로 보내지고, CPU는 대기 중인 다음 프로세스로 넘어감
- 균등한 CPU 점유 시간을 보장하며, 시분할 시스템을 사용
- ```Time Quantum```가 클 경우에는 비선점 스케줄링 방식 중 하나인 FCFS 방식과 비슷해짐

#### 3. Multi Level Queue
![](https://velog.velcdn.com/images/imeyh/post/eb269f56-cef1-4228-a7fd-7c20bd77528a/image.png)
- 프로세스들을 여러 종류 그룹으로 분할하여 각 그룹마다 다른 Ready Queue를 이용하며 상위 단계의 작업이 CPU를 선점
- 큐마다 다른 스케줄링 알고리즘을 사용

#### 4. Multi Level Feedback Queue
![](https://velog.velcdn.com/images/imeyh/post/9208ddc6-a5b7-4e93-961b-131d5bf5e1b2/image.png)
- 기본 개념은 Multi Level Queue와 동일하지만, 프로세스가 다른 큐로 이동 가능
- 모든 새로운 프로세스는 가장 높은 우선순위를 가진 Ready Queue에 들어가는데, ```Time Quantum```를 다 채운 프로세스는 한단계 낮은 우선순위의 Ready Queue로 이동
- Ready Queue의 우선순위가 낮을 수록 ```Time Quantum```을 크게 줌으로써 보완
- 가장 마지막 Ready Queue는 보통 FCFS 방식을 채택
- 유연성이 뛰어나며, ```Turnaround Time```과 ```Response Time```에 최적화

## 비선점형(Non-Preemptive) 스케줄링
- 프로세스가 CPU를 점유하고 있다면 작업 종료 후 CPU 반환 시까지 다른 프로세스는 CPU를 점유할 수 없는 방식

### 장점
- 모든 프로세스들에게 공정
- 응답 시간 예측 가능

### 단점
- 짧은 작업을 수행하는 프로세스라도 긴 작업이 종료될 때까지 기다려야 함(상황에 따라 효율성 차이 多)

### 종류
#### 1. FCFS(First Come First Served)
![](https://velog.velcdn.com/images/imeyh/post/83138510-0ce4-446b-a684-d3af4c8d1285/image.png)
- 프로세스가 Ready Queue에 도착한 순서에 따라 CPU를 할당받음
 
#### 2. SJF(Shortest Job First)
![](https://velog.velcdn.com/images/imeyh/post/e5302703-3652-449d-9144-95463adce7e8/image.png)
- Ready Queue에 있는 프로세스들 중 가장 작은 실행시간을 가진 프로세스가 종료 시까지 CPU 할당받음
- CPU 요구시간이 긴 작업과 짧은 작업 간의 불평등이 심하여, CPU 요구시간이 긴 프로세스는 기아 현상 발생

#### 3. HRN(Highest Response Ratio Next)
- 대기 중인 프로세스 중 현재 ```Response Ratio```가 가장 높은 것을 선택
- 긴 작업과 짧은 작업 간의 불평등을 완화  → SJF의 단점 보완
> Response Ratio = (대기시간 + 서비스시간) / 서비스시간
