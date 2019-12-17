## 자료형

자바에서는 자료형을 크게 2가지로 나뉜다.

- 기본 자료형
  - byte, short, int, long, char, float, double, boolean
- 참조 자료형
  - new로 객체를 생성

<br/>

기본 자료형은 stack 메모리에 실제 값이 저장 된다.

```java
int a = 10; // stack 메모리에 10이라는 값이 저장.
System.out.println(a); // 10
```

<br/>

반면에 참조 자료형은 heap 메모리에 실제 값이 저장되고 변수는 메모리 주소값을 받는다.

```java
class People{
  String name;
}


People p = new People();
System.out.println(p); // People@77459877
```

