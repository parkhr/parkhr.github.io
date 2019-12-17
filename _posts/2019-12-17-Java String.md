---
published: true
layout: single
title: "Java String"
category:
  - Java
date : 2019-12-17 18:25:00

---

## String

자바에서 String은 특별한 참조 자료형이다.

String 객체는 new 생성자를 이용해서 생성할 수 있고, 두 개의 큰 따옴표 안에 값을 입력하여 생성할 수도 있다.

<br/>

new 생성자를 이용하여 인스턴스를 만들고 heap  메모리에서 관리 하는건 다른 참조 자료형과 다를게 없다.

```java
String str = new String("str");
```

<br/>

![](/assets/images/Java_String메모리.png)

<br/>

하지만 참조 자료형과는 다른 immutable의 특징을 가지고 있다. 즉, 한번 객체가 생성되어 저장된 값은 변하지 않는다.

```java
String s3 = new String("cat");
s3 = s3 + s3; // catcat 값을 가지는 String 객체를 새로 생성하고, s3는 그 인스턴스를 참조하게 된다.
```

<br/>

String 연산은 새로운 객체를 계속 만들기 때문에 메모리 관리 측면에서 비효율적이다.

그래서 만들어진 메모리 영역이 String Constant Pool이다. 이 메모리 영역은 기존에 만들어진 문자열 값이 저장되어 있다.

```java
String s1 = "cat";
String s2 = "cat";
// " " 로 생성된 같은 값을 가지는 String 객체는 같은 주소를 가지게 된다.
System.out.println(s1 == s2); // true
System.out.println(s1 == s3); // false
```

