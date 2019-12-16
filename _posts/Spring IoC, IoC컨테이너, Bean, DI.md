---
published: true
layout: single
title: "Spring IoC, IoC컨테이너, Bean, DI"
category:
  - Spring
date : 2019-12-16 16:25:00

---

## 의존성 역전(Inversion of Control)

<br/>

*객체간의 결합도란?*

예를들어 Player는 Weapon 클래스의 객체를 꼭 가지고 있어야 한다고 가정할 때, 이것을 나타내는 용어가 *의존성*이라 한다.

또한 의존성은 new 키워드로 이루어진다.

```java
class Player{
	private Weapon weapon;
	
	void setWeapon(){
        this.weapon = new Weapon();
	}
}
```

하지만 위와 같은 방식은 코드의 유연성을 떨어트리고 중복 및 가독성이 떨어지는 원인이 된다.

<br/>

그래서 의존성 역전을 이용하여 이러한 문제점들을 해결한다.

```java
class Player{
	private Weapon weapon;
    
    Player(Weapon weapon){
        this.weapon = weapon; // 의존성이 역전됨.
    }
}
```

<br/>

## IoC 컨테이너(Container)

스프링에서는 컨테이너라는 곳에서 **Bean**이라는 객체를 만들고 엮어주며 제공해준다.

이런 의존성을 주입시키는 행위를 DI(Dependency Injection)라고 부른다.

IoC 컨테이너에 있는 Bean들 끼리만 의존성을 주입해준다.

<br/>



## Bean

Bean의 범위는 2가지로 나뉜다.

- 싱글턴(Singleton) : 하나 유일한 인스턴스를 제공하는 방식이다.
- 프로토타입(Prototype) : 다른 인스턴스들을 생성해서 제공하는 방식.

<br/>



## 의존성 주입(DI, Dependency Injection)

의존성 주입은 객체가 필요로하는 어떤 객체를 생성자 또는 setter를 통해서 주입하는 것을 말한다.

- @Autowired
  - 필드, setter, 생성자 모두 어노테이션을 붙일 수 있다.
  - 생성자로 주입하는 것을 권장한다.
- @Resource
  - bean의 id속성을 기준으로 프로퍼티의 이름을 찾아서 의존성을 주입한다.
- @Inject
  - 생성자를 제외한 setter 및 필드에 어노테이션을 붙일 수 있다.



<br/>

## 스프링 MVC 모델

스프링 MVC는 Model2 방식을 따른다.

DispatcherServlet이 Client요청을 받는다. -> HandlerMapping이 알맞는 Controller를 찾는다.

HandlerMapping에 실행할 Controller의 메서드를 찾는다. -> Contoller의 메서드를 실행하며 그 결과 Model를 DispatcherServelt에 반환

ViewResolver는 알맞은 JSP파일을 찾는다. -> View는 JSP파일을 Model의 정보를 토대로 Client에 반환

