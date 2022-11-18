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

### Q2. 접근 지시자를 사용하는 이유는 무엇일까요? SOLID(객체 지향 설계)와 관련해 설명해주세요. 