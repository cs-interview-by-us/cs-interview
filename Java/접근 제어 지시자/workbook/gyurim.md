# 접근 제어 지시자

### Q1. 다음 자바 코드의 결과를 설명해주세요.
- house/HousePark.java
```Java
package house;  

public class HousePark {
    String lastname = "park";
}
```
- house/person/EungYongPark.java
```Java
package house.person; 

import house.HousePark;

public class EungYongPark extends HousePark {  
    
    public static void main(String[] args) {
        EungYongPark eyp = new EungYongPark();
        System.out.println(eyp.lastname); 
    }
}
```
- default 접근 제어자는 동일 패키지 내에서만 접근이 가능합니다.
- EungYongPark 클래스와 HousePark 클래스는 패키지가 다르기 때문에 **컴파일 오류가 발생**합니다. 

### Q2. 접근 지시자를 사용하는 이유는 무엇일까요? SOLID(객체 지향 설계)와 관련해 설명해주세요. 

- 외부로부터의 접근을 제한하여 데이터를 보호하는 은닉성을 위해 접근 제어 지시자를 사용합니다. 
- 외부에는 불필요하고 내부적으로만 사용되는 부분을 감추는 캡슐화를 위해 접근 제어 지시자를 사용합니다. 