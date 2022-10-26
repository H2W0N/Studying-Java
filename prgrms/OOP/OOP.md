# Object Oriented Programming

## 1. 객체지향 프로그래밍
- JAVA : 객체지향 언어다! 하고 등장.
- 객체지향 프로그래밍이란?
  - 프로그램을 객체로 구성하는것.
  - 등장 배경 : 프로그램이 거대화하며 등장.
  - 아이디어 : 어떻게 큰 프로그램을 만들것인가?
    - 해결책 : 작게 나눠서 만들고 합친다.
- 프로그램의 동작을 객체들에게 나눠서 수행시킨다.
- 개념적인 용어 : 객체 / 기술적인 용어 : class, instance
  - 클래스가 객체냐, 인스턴스가 객체냐 (X)
- 객체는 작은 기능을 수행.
- 객체와 객체는 서로 협력관계
- => 일을 잘게 쪼개서 객체에게 위임하고, 서로 협력하게 만드는 것.
- 객체를 서로 구분할 필요가 있음
  - type(형)으로 구분
    - `String str = "Hello World"`
  - type 만들기 : class 만들기
```java
package com.prgrms;

import java.lang.*;

class MyObject extends Object implements Runnable {
    // 필드영역
    private int a = 0;
    // 메소드 영역
    public void run() {
        a += 1;
    }
    
} // 이게 하나의 객체

MyObject obj = new MyObject();
```

## 2. 객체지향의 특성

### (1) 캡슐화
1. 캡슐처럼 완성도가 있다.
- 객체는 기능을 수행하는 최소단위로써 완전함을 갖는다.
2. 정보가 은닉되어 있다.
- 객체의 정보가 밖으로 전달되거나 밖에서 객체 내의 정보에 접근하지 못하게 한다.

=> 객체는 스스로 동작할 수 있는 환경을 갖고 있어야 한다. 외부에 의존하거나 외부의 침략을 제한하여야 한다.
```java
class Human {
    private Heart heart;
    private Blood blood;
    protected Gene gene;
    
    Blood donation() {
        return null;
    }
}

Human h = new Human();
// h.heart.stop(); 같은 외부의 접근을 차단

h.donation();

class Child extends Human {
    void run() {
        this.gene;
    }
}
```

- 접근지정자
  - private : 객체 소유
  - protected : 상속된 객체에서도 접근 가능.
  - (friendly) : 같은 패키지 내에서 접근 가능. (패키지 가시성)
  - public : 모두 다 접근 가능.
```java
com.prgrms
com.prgrms.girl
              Secret
com.prgrms.boy
              Secret
```  

### (2) 상속
- 상위, 부모, super, [추상]
- 하위, 자식, (this), [구체]

- **오해** : 공통된 기능을 여러 객체에게 전달하고 싶을 때 사용?
  - `원자 > 물질 > 생물 > 동물 > 포유류 > 사람 > 남자 > 짱구`

### (3) 추상화
- 추상화된 객체 : 추상체
- 구체적인 객체 : 구상체
- 객체간의 관계에서 상위에 있는것이 항상 하위보다 추상적이어야 한다.
```java
// 의미적 추상체
class Login {
    void login();
}

class KakaoLogin() extends Login {
    void login();
}
```

```java
// 추상기능을 가진 객체
abstract class Login {
  abstract void login();
}

class KakaoLogin extends Login {
  void kakao() {}
  @Override 
  void login() {}
}
}
```

```java
// 객체 자체가 추상적
interface Login {
  void login();
}

class KakaoLogin implements Login {
  void kakao() {}
  @Override 
  void login() {}
}
```

### (4) 다형성
- 형(type)을 여러가지로 표현할 수 있다.
```java
class KakaoLogin implements Login {
  void kakao() {}
  @Override 
  void login() {}
}

interface Portal {
  void portal();
}

class NaverLogin implements Login, Portal {
  void naver() {}
  @Override 
  void login() {}
  @Override 
  void portal() {}
}

  KakaoLogin k = new KakaoLogin();
  Login k = new KakaoLogin();
```

```java
Login login = new Login();
Login login = new KakaoLogin();
Login login = new NaverLogin();
login.login();

Portal potal = new NaverLogin();
potal.portal();
```
