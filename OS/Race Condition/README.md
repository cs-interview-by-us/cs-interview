# Race Condition(경쟁 상태)
## Race Condition이란?
- 여러 프로세스가 공유 자원에 동시에 접근할 때, 공용 데이터에 대한 접근 순서에 따라 결과값에 영향을 줄 수 있는 상황
- 동시 접근 시 자료의 일관성을 해치는 결과가 나타남
- 임계 영역에 대한 프로세스들의 동시적인 접근을 잘 제어한다면 Race Condition(경쟁 상태)을 해결 가능

> ## Critical Section(임계 영역)
> - 운영체제에서 여러 프로세스가 데이터를 공유하면서 수행될 때 각 프로세스에서 공유 자원에 접근하는 프로그램 코드 부분
> ### 임계 영역 문제를 해결하기 위해 충족해야하는 조건
> #### 1. Mutual Exclusion(상호 배제)
> - 한 프로세스가 임계 영역을 수행 중이라면 다른 모든 프로세스들은 그 임계 영역에 들어가지 못하게 막는 것
> 
> #### 2. Progress(진행)
> - 임계 영역에 들어간 프로세스가 없는 상태에서 임계 영역에 들어가려는 프로세스가 있을 시 들어가게 해줘야 함  
> 즉, 임계 영역에 있는 프로세스 외에는 다른 프로세스가 임계 영역에 진입하는 것을 방해하면 안됨  
>
> #### 3. Bounded Waiting(한정 대기)
> - Starvation(기아 상태)를 방지하기 위해 프로세스가 임계 영역에 들어가려고 요청한 후부터 다른 프로세스들이 임계 영역에 들어가는 횟수에 한계가 있어야 함  
> 임계 영역에 한 번 들어갔다 나온 프로세스는 다음에 들어갈 때 제한을 둠  

## Race Condition 발생상황
### 1. 커널안에 코드를 수행하는 중 인터럽트 발생
- 커널 안에 있는 변수를 증가시키는 중 인터럽트가 발생하여 인터럽트 처리 함수(함수 코드는 커널에 존재)에서는 해당 변수를 감소시킬 때 변수의 결과값에 문제가 발생
- 사용자 프로세스는 해당 프로세스에 할당받은 메모리에만 존재할 수 있지만 커널은 서로 다른 프로세스가 공유하기 때문에 발생
> 해결방법: 작업을 할 때 인터럽트 발생하더라도 작업이 완료된 후 인터럽트가 발생하도록 처리순서를 부여

### 2. 프로세스가 System Call를 호출하여 커널 모드로 수행 중일 때 Context Switch가 발생
- 사용자 프로세스가 System Call를 호출하면 커널 모드로 커널안에 존재하는 변수를 수정 가능  
할당된 CPU 사용시간이 만료되면 Context Switch가 발생하는데 새롭게 CPU를 할당받은 사용자 프로세스가 이전 프로세스와 동일한 System Call를 호출하여 수정하고 있던 변수에 대한 작업을 수행할 때 결과적으로 변수값에 문제가 발생
> 해결방법: 사용자 프로세스가 System Call를 호출하여 커널모드의 작업을 완료한 후 종료될 때 Context Switch가 발생할 수 있게 함  
즉, 커널모드에 있다면 CPU의 제어권을 빼앗지 않음  

### 3. 여러 프로세스의 공유 메모리 내 커널 안 변수에 접근
- CPU가 여러 개인 시스템에서 공유 메모리 속 데이터를 여러 프로세스가 접근할 때 발생
> 해결방법: 커널 안 변수에 접근할 때 lock/unlock을 걸어 매 순간 변수에 접근하는 프로세스는 1개로 한정