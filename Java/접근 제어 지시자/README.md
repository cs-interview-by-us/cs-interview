# 접근 제어 지시자 (Access Modifier)
> 클래스 외부에서 클래스의 멤버 변수, 메서드, 생성자를 사용할 수 있는지 여부를 지정하는 키워드

## public 
> 어디서든 접근 가능합니다. 

## private
> 같은 클래스 내부에서만 접근 가능합니다. 
> 외부 클래스, 상속 관계의 클래스에서도 접근 불가합니다. 

## default
> 접근 제어 지시자를 선언하지 않은 경우, 동일 패키지 내에서만 접근이 가능합니다.
> 상속 관계라도 패키지가 다르면 접근 불가합니다. 

### 패키지
- 비슷한 성격의 자바 클래스들을 모아 놓은 자바의 디렉토리입니다. 
```Java
package house;

public class HouseKim {
    // 파일의 위치: src/house/HouseKim.java
}
```

```Java
package house.person; // house 패키지의 하위 패키지 

public class EungYongPark {
    // 파일의 위치: src/house/person/EungYongPark.java
}
```

- 장점
    - 클래스의 분류가 용이합니다.
    - 패키지가 다르다면 동일한 클래스 명을 사용할 수 있습니다. 

## protected
> 동일 패키지나 상속 관계의 클래스에서만 접근 가능하고 그 외 외부에서는 접근이 불가합니다. 

<img width="704" alt="access modifier" src="https://user-images.githubusercontent.com/31344894/202730719-48d9b566-f47c-4691-ac7f-d49cbcb7f98e.png">


