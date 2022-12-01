****Q1. 다음 자바 코드의 결과를 String 객체와 String 리터럴와 관련하여 설명해주세요.****

```java
String str = "bepoz";
String str2 = "bepoz";
String str3 = new String("bepoz");
System.out.println(str==str2); //true
System.out.println(str==str3); //false
```

`String str1 = "bepoz";` 는 문자열 리터럴 생성법이고, `String str3 = new String("bepoz")` 는 new 연산자를 이용한 생성법이다.

new 연산자는 메모리의 **heap** 영역에 할당되고 리터럴 방식은 **String Constant Pool** 영역에 할당된다.

str 와 str2는 **String Constant Pool**에서 같은 참조 값을 가지고 오기 때문에 리터럴은 내부적으로 `intern()` 메서드를 호출한다.`intern()` 메서드는 해당 문자열을 pool 에서 찾고 있으면 해당 참조 값을 가지고오고 그렇지 않다면 새로 집어넣고 해당 주소 값을 반환해준다.

![Untitled](https://user-images.githubusercontent.com/22094204/205069099-804ffbda-2273-4e0f-93e4-12629c2f9411.png)