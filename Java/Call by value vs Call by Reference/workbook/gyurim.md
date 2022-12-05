# Call by value vs Call by Reference

### Q1. 자바는 Call by Value와 Call by Reference 중 어떤 것인가요? 그 이유에 대해 설명해주세요.
- 자바는 Call by Value를 사용해 파라미터를 넘깁니다.
    - 원시 타입을 넘길 때는 값만 전달하는 call by value로 동작합니다.
    - 참조 타입을 넘길 때는 **주소를 가리키는 참조값**을 복사해서 전달하는 call by value로 동작합니다. 따라서 복사된 주소 값으로 참조가 가능하므로 주소 값이 가리키는 객체의 내용이 변경됩니다. 
        - 참조값: 객체의 메모리를 생성했을 때 메모리와 연결된 유일한 숫자값 

> # 작동 방식 
>
> ## 원시(기본)형 
> 자바의 원시 자료형은 스택 영역에 저장이 됩니다. 
> 
> <img width="788" alt="prim java" src="https://user-images.githubusercontent.com/31344894/205735602-4236c4b7-d9d9-4860-b201-4b36c402b722.png">
> 
> <img width="282" alt="primitive" src="https://user-images.githubusercontent.com/31344894/205733408-25fcf735-8e64-43dd-b905-db406bd3002d.png">
> 
> 따라서 main 함수에서 jack = 1, coding = 1 변수를 생성하고 인자값으로 changeJackCoding 함수에 해당 변수들을 넘겼다면,  
> 변수의 값들이 전달되기 때문에 jack, coding 변수가 아닌 지역 변수(a, b)에 값만 복사가 되어 생성됩니다.  
> 
> <img width="279" alt="primitive 2" src="https://user-images.githubusercontent.com/31344894/205733419-8bbb063d-1745-46cf-bc4f-d13ca650e22a.png">
> changeJackCoding 함수가 종료되면 a, b 변수는 스택 영역에서 사라집니다. 
> 
> 자바의 기본형은 이렇게 call by value로 작동이 됩니다. 
>
> ## 참조형
> 자바의 참조형의 경우 값이 힙 영역에 저장이 됩니다.
> 힙은 스택과 달리 프로세스 전역에서 공유하는 공간이며 모든 객체들은 힙 영역에 저장됩니다. 
> 
> <img width="792" alt="ref java" src="https://user-images.githubusercontent.com/31344894/205735611-c84d2328-5cb4-41ff-afbb-aaede1296946.png">
> 
> <img width="788" alt="ref" src="https://user-images.githubusercontent.com/31344894/205734864-5c34f648-5bee-42ec-b13e-be82c8576276.png">
> 
> 먼저 JackCoding 객체의 인스턴스 jack을 생성하면, 참조 변수와 참조값이 stack에 생성되고 실제 인스턴스의 값은 Heap 영역에 생성됩니다.
> 그리고 changeJackCoding 함수가 실행되면서 새로 coding이라는 이름을 가진 JackCoding 객체의 새로운 인스턴스를 생성하고 param에 넣습니다. 
> 
> 따라서 이 메서드를 빠져나왔을 때, jack 참조 변수는 기존에 자신이 보던 객체를 참조하고 있는 것입니다. 
>
> ### 만약 메서드에 참조값을 넣어서 값을 변경하고 싶다면? 
> 메서드 내에서 객체를 새로 생성하지 말고 참조값을 사용하면 됩니다. 
> <img width="789" alt="refe java" src="https://user-images.githubusercontent.com/31344894/205736581-b2c7e647-afc9-4d23-a91b-7e0d2350ec88.png">
> changeJackCoding 메서드에서 새로운 인스턴스를 생성하지 않고 기존에 받은 객체의 값을 변경하는 코드입니다. 
> <img width="781" alt="refe" src="https://user-images.githubusercontent.com/31344894/205736590-161345cc-3d9a-4799-9a4b-11cb8174b474.png">
> 
> jack 인스턴스를 생성하면 참조 변수 jack과 참조값 6cd8737이 스택 영역에 저장되고 객체 값은 힙 영역에 저장됩니다.
> changeJackCoding 메서드가 실행되면 매개변수로 들어간 참조값 6cd8737이 복사되고 참조 변수 param과 참조값 6cd8737이 스택 영역에 들어갑니다.
> 결국 참조값이 같으므로 두 참조 변수는 Heap 영역의 같은 값을 바라보고 있습니다.
> 
> <img width="794" alt="refe 2" src="https://user-images.githubusercontent.com/31344894/205736586-f51cfa21-9718-4bb5-a98d-cfdceb2f6fa9.png"> 
> 
> 따라서 param의 값을 변경하면 jack도 같은 값을 바라보고 있으므로 변경이 됩니다. 
>
> ## 결국 자바의 기본형이든 참조형이든 모두 call by value 방식으로 작동이 됩니다. 
> 메서드의 매개변수는 모두 값이 복사되어 stack에 쌓입니다. 


- [참고](https://jackjeong.tistory.com/37)

### Q2. Call by Value와 Call by Reference 장단점을 설명해주세요.
- Call by Value
    - 장점 : 복사하여 처리하기 때문에 안전하다. 원래의 값이 보존이 된다.
    - 단점 : 복사를 하기 때문에 메모리가 사용량이 늘어난다.
- Call by Reference
    - 장점 : 복사하지 않고 직접 참조를 하기에 빠르다.
    - 단점 : 직접 참조를 하기에 원래 값이 영향을 받는다.