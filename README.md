# cs-interview 🍀
참고: 
- https://github.com/gyoogle/tech-interview-for-developer
- https://github.com/WooVictory/Ready-For-Tech-Interview

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
    - 질문지는 주제명 폴더 내에 workbook 폴더 속에 README.md로 올리기
    - 답변 제출할 때는 workbook 폴더에 자신의 이름.md로 올리기
- 커밋 컨벤션
    - [과목명/정리] 주제 로 commit
        - 예시: [OS/정리] 운영체제란
    - workbook 올릴 땐, [과목명/워크북] 로 commit
    - workbook 제출할 땐, [과목명/워크북 제출] 로 commit
    - 수정할 땐, 수정하고 싶은 커밋 메세지 앞에 "fix: "를 붙여서 fix: [과목명/워크북] 로 commit
- 브랜치 컨벤션
    - workbook/이름 
        - 예시: workbook/gyurim
## CS-Interview Topic 
- OS
    - [운영체제란](https://github.com/cs-interview-by-us/cs-interview/tree/main/OS/%EC%9A%B4%EC%98%81%EC%B2%B4%EC%A0%9C%EB%9E%80)
    - [프로세스 vs 스레드](https://github.com/cs-interview-by-us/cs-interview/tree/main/OS/%ED%94%84%EB%A1%9C%EC%84%B8%EC%8A%A4%20vs%20%EC%8A%A4%EB%A0%88%EB%93%9C) 
    - [프로세스 주소 공간](https://github.com/cs-interview-by-us/cs-interview/tree/main/OS/%ED%94%84%EB%A1%9C%EC%84%B8%EC%8A%A4%20%EC%A3%BC%EC%86%8C%EA%B3%B5%EA%B0%84)
    - [인터럽트(Interrupt)](https://github.com/cs-interview-by-us/cs-interview/tree/main/OS/%EC%9D%B8%ED%84%B0%EB%9F%BD%ED%8A%B8(Interrupt))
    - [시스템 콜(System Call)](https://github.com/cs-interview-by-us/cs-interview/tree/main/OS/%EC%8B%9C%EC%8A%A4%ED%85%9C%20%EC%BD%9C(System%20Call))
    - [PCB와 Context Switching](https://github.com/cs-interview-by-us/cs-interview/tree/main/OS/PCB%EC%99%80%20Context%20Switching)
    - [IPC(Inter Process Communication)](https://github.com/cs-interview-by-us/cs-interview/tree/main/OS/IPC(Inter%20Process%20Communication))
    - [CPU 스케줄링](https://github.com/cs-interview-by-us/cs-interview/tree/main/OS/CPU%20%EC%8A%A4%EC%BC%80%EC%A4%84%EB%A7%81)
    - [데드락(DeadLock)](https://github.com/cs-interview-by-us/cs-interview/tree/main/OS/%EB%8D%B0%EB%93%9C%EB%9D%BD(DeadLock))
    - Race Condition
    - [세마포어(Semaphore) & 뮤텍스(Mutex)](https://github.com/cs-interview-by-us/cs-interview/tree/main/OS/%EC%84%B8%EB%A7%88%ED%8F%AC%EC%96%B4(Semaphore)%20%26%20%EB%AE%A4%ED%85%8D%EC%8A%A4(Mutex))
    - 페이징 & 세그먼테이션 (PDF)
    - 페이지 교체 알고리즘
    - [메모리(Memory)](https://github.com/cs-interview-by-us/cs-interview/tree/main/OS/%EB%A9%94%EB%AA%A8%EB%A6%AC(Memory))
    - 파일 시스템

- Network
    - [OSI 7 계층](https://github.com/cs-interview-by-us/cs-interview/tree/main/Network/OSI%207%20%EA%B3%84%EC%B8%B5)
    - [TCP 3 way handshake & 4 way handshake](https://github.com/cs-interview-by-us/cs-interview/tree/main/Network/TCP%203%20way%20handshake%20%26%204%20way%20handshake)
    - [TCP/IP 흐름제어 & 혼잡제어](https://github.com/cs-interview-by-us/cs-interview/tree/main/Network/TCP%20IP%20%ED%9D%90%EB%A6%84%EC%A0%9C%EC%96%B4%20%26%20%ED%98%BC%EC%9E%A1%EC%A0%9C%EC%96%B4)
    - [UDP](https://github.com/cs-interview-by-us/cs-interview/tree/main/Network/UDP)
    - [대칭키 & 공개키](https://github.com/cs-interview-by-us/cs-interview/tree/main/Network/%EB%8C%80%EC%B9%AD%ED%82%A4%20%26%20%EA%B3%B5%EA%B0%9C%ED%82%A4)
    - [HTTP & HTTPS](https://github.com/cs-interview-by-us/cs-interview/tree/main/Network/HTTP%20%26%20HTTPS)
    - [TLS/SSL handshake](https://github.com/cs-interview-by-us/cs-interview/tree/main/Network/TLS%20%26%20SSL%20handshake)
    - [로드 밸런싱(Load Balancing)](https://github.com/cs-interview-by-us/cs-interview/tree/main/Network/%EB%A1%9C%EB%93%9C%EB%B0%B8%EB%9F%B0%EC%8B%B1(Load%20Balancing))
    - [Blocking, Non-blocking & Synchronous,Asynchronous](https://github.com/cs-interview-by-us/cs-interview/tree/main/Network/Blocking%2C%20Non-blocking%20%26%20Synchronous%2C%20Asynchronous)
    - [Blocking & Non-Blocking I/O](https://github.com/cs-interview-by-us/cs-interview/tree/main/Network/Blocking%20%26%20Non-Blocking%20IO)

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
   
- Java
    * [Call by value ve Call by Reference](https://github.com/cs-interview-by-us/cs-interview/tree/main/Java/Call%20by%20value%20ve%20Call%20by%20Reference)
    * [String, StringBuilder, StringBuffer 차이](https://github.com/cs-interview-by-us/cs-interview/tree/main/Java/String%2C%20StringBuilder%2C%20StringBuffer%20%EC%B0%A8%EC%9D%B4)
    * [객체지향 프로그래밍](https://github.com/cs-interview-by-us/cs-interview/tree/main/Java/%EA%B0%9D%EC%B2%B4%EC%A7%80%ED%96%A5%20%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D)
    * [접근 제어 지시자](https://github.com/cs-interview-by-us/cs-interview/tree/main/Java/%EC%A0%91%EA%B7%BC%20%EC%A0%9C%EC%96%B4%20%EC%A7%80%EC%8B%9C%EC%9E%90)
    * ==와 equals() 차이
    * Wrapper Class
    * 기본형과 참조형의 차이점
    * 오버라이딩과 오버로딩
    * final 키워드
    * non-static 멤버와 static 멤버 차이
    * 추상 클래스
    * 인터페이스
    * 추상 클래스와 인터페이스의 차이
    * 변수의 종류와 메모리 구조
    * Reflection
    * Garbage Collection
    * Java에서 Thread
    * Java의 String
    * int와 short
    * JVM
    * equals() 메소드 동작 원리
    * Integer vs int size 비교
    * SOLID 원칙 
    * 자바의 컬렉션 프레임워크
    
