# String, StringBuilder, StringBuffer 차이

### Q1. 다음 자바 코드의 결과를 String 객체와 String 리터럴와 관련하여 설명해주세요.

```Java
String str = "bepoz";
String str2 = "bepoz";
String str3 = new String("bepoz");
System.out.println(str==str2);
System.out.println(str==str3); 
```
- 먼저 자바에서 참조타입의 == 연산자는 주소를 비교하는 연산자입니다. 
- ```String str1 = new String("abc")```은 new 연산자를 이용한 생성법이고 메모리의 heap 영역에 할당됩니다. 
- ```String str2 = "abc"```은 문자열 리터럴 생성법이고 이는 String Constant Pool 영역에 할당됩니다. 
- str과 str2 변수는 해당 문자열을 String Constant Pool에서 같은 참조값을 가지고 오기 때문에 ```true```를 리턴합니다. 
- str과 str3은 서로 다른 영역에 할당이 되어있기 때문에 ```false``를 리턴합니다. 