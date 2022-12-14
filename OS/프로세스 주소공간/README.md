## 프로세스 주소공간
프로세스가 실행 중에 접근할 수 있도록 허용된 주소의 최대범위로 코드, 데이터, 힙 스택 4요소들을 합쳐 프로세스가 엑세스 할 수 있는 사용자 공간의 메모리 영역을 포함한다.

프로그램이 CPU에 의해 실행됨 → 프로세스가 생성 & **프로세스 주소 공간**이 할당됨
<img src="https://user-images.githubusercontent.com/22094204/198679885-57dd91a8-2971-4833-9f51-fb1d37fd8095.png" width="500" height="350"/>

< 프로세스 주소 공간 >

<img src="https://user-images.githubusercontent.com/22094204/198679126-450b0fc2-b102-4ba3-bcd5-19c19025c651.png" width="200" height="400"/>

- **Text(Code)** Segment : 프로그램 소스 코드 저장
- **Data** Segment : 전역 변수 저장
- **Heap** Segment : 동적할당된 객체 저장(런타임에 크기가 결정되는 영역, 참조형 데이터(ex. class) 할당됨)
- **Stack** Segment : 함수, 지역 변수 저장  
  
    
< 예시 >

![Untitled](https://user-images.githubusercontent.com/22094204/198679298-9436673a-a8a6-4ff5-a90e-062fd5d26423.png)

```
프로그램의 함수와 지역 변수는, LIFO(가장 나중에 들어간게 먼저 나옴)특성을 가진 스택에서 실행된다.
따라서 이 함수들 안에서 공통으로 사용하는 '전역 변수'는 따로 지정해주면 메모리를 아낄 수 있다.
```

## 예상질문

- 프로세스 주소공간의 4가지 영역은?
- 프로세스 주소공간을 나누는 이유는?
