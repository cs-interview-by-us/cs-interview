****Q1. 다음 자바 코드의 결과를 설명해주세요.****

- house/HousePark.java

```java
package house;

public class HousePark {
    String lastname = "park";
}
```

- house/person/EungYongPark.java

```java
package house.person; 

import house.HousePark;

public class EungYongPark extends HousePark {  
    
    public static void main(String[] args) {
        EungYongPark eyp = new EungYongPark();
        System.out.println(eyp.lastname); 
    }
}
```

HousePark 클래스를 상속한 EungYongPark 클래스의 패키지는 `house.person`으로 HousePark의 패키지인 `house`와 다르지만 HousePark의 lastname 변수가 ****default****이기 때문에 컴파일 오류가 발생할 것이다.

****Q2. 접근 지시자를 사용하는 이유는 무엇일까요? SOLID(객체 지향 설계)와 관련해 설명해주세요.****

- 외부로부터의 접근을 제한하여 데이터를 보호하기 위함. 객체지향 개발방법론에서는 이를 '**은닉성**'이라고 표현함
- 외부에는 불필요하고 내부적으로만 사용되는 부분을 감추기 위함. 객체지향 개발방법론에서는 이를 '**캡슐화**'라고 표현함