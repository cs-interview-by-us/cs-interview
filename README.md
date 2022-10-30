# cs-interview 🍀
참고: https://github.com/gyoogle/tech-interview-for-developer

## 스터디 방식
- 매주 과목을 정함
- 정한 과목의 주제 3가지를 각자 담당
- 금요일까지 **담당한 주제를 공부한 내용 정리본 및 인터뷰 예상 질문**을 작성해 commit
- repository README.md에 정리본 링크 연결하기 
- 주말 동안 올라온 예상 질문들에 대한 답을 작성해 PR로 제출
- 답변에 대해 필요하다면 코멘트를 남기고, 주제 담당자가 확인해서 merge 

## 제출
- 파일 구조
    - 각 과목에 주제명으로 폴더를 만든 후, 정리한 내용을 README.md로 올리기 
    - 질문지는 주제명 폴더 내에 Workbook 폴더 속에 README.md로 올리기
    - 답변 제출할 때는 Workbook 폴더에 자신의 이름.md로 올리기
- 커밋 컨벤션
    - [과목명/정리] 주제 로 commit
        - 예시: [OS/정리] 운영체제란
    - Workbook 올릴 땐, [과목명/워크북] 로 commit
    - Workbook 제출할 땐, [과목명/워크북 제출] 로 commit
    - 수정할 땐, 수정하고 싶은 커밋 메세지 앞에 "fix: "를 붙여서 fix: [과목명/워크북] 로 commit
- 브랜치 컨벤션
    - workbook/이름 
        - 예시: workbook/gyurim
## CS-Interview Topic 
- OS
    - 운영체제란
    - [프로세스 vs 스레드](https://github.com/cs-interview-by-us/cs-interview/tree/main/OS/%ED%94%84%EB%A1%9C%EC%84%B8%EC%8A%A4%20vs%20%EC%8A%A4%EB%A0%88%EB%93%9C) 
    - [프로세스 주소 공간](https://github.com/cs-interview-by-us/cs-interview/tree/main/OS/%ED%94%84%EB%A1%9C%EC%84%B8%EC%8A%A4%20%EC%A3%BC%EC%86%8C%EA%B3%B5%EA%B0%84)
    - 인터럽트(Interrupt)
    - 시스템 콜(System Call)
    - PCB와 Context Switching
    - IPC(Inter Process Communication)
    - CPU 스케줄링
    - 데드락(DeadLock)
    - Race Condition
    - 세마포어(Semaphore) & 뮤텍스(Mutex)
    - 페이징 & 세그먼테이션 (PDF)
    - 페이지 교체 알고리즘
    - 메모리(Memory)
    - 파일 시스템

- Network
    - [OSI 7 계층](https://github.com/cs-interview-by-us/cs-interview/tree/main/Network/OSI%207%20%EA%B3%84%EC%B8%B5)
    - [TCP 3 way handshake & 4 way handshake](https://github.com/cs-interview-by-us/cs-interview/tree/main/Network/TCP%203%20way%20handshake%20%26%204%20way%20handshake)
    - TCP/IP 흐름제어 & 혼잡제어
    - UDP
    - 대칭키 & 공개키
    - HTTP & HTTPS
    - TLS/SSL handshake
    - 로드 밸런싱(Load Balancing)
    - Blocking, Non-blocking & Synchronous,Asynchronous
    - Blocking & Non-Blocking I/O

- Algorithm
    - 거품 정렬(Bubble Sort)
    * 선택 정렬(Selection Sort)
    * 삽입 정렬(Insertion Sort)
    * 퀵 정렬(Quick Sort)
    * 병합 정렬(Merge Sort)
    * 힙 정렬(Heap Sort)
    * 기수 정렬(Radix Sort)
    * 계수 정렬(Count Sort)
    * 이분 탐색(Binary Search)
    * 해시 테이블 구현
    * DFS & BFS
    * 최장 증가 수열(LIS)
    * 최소 공통 조상(LCA)
    * 동적 계획법(Dynamic Programming)
    * 다익스트라(Dijkstra) 알고리즘
    * 비트마스크(BitMask)

- Database
    - 키(Key) 정리
    * SQL - JOIN
    * SQL Injection
    * SQL vs NoSQL
    * 정규화(Nomalization)
    * 이상(Anomaly)
    * 인덱스(INDEX)
    * 트랜잭션(Transaction)
    * 트랜잭션 격리 수준(Transaction Isolation Level)
    * 저장 프로시저(Stored PROCEDURE)
    * 레디스(Redis)
