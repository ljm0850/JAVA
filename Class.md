# Class

### void

- 반환 값이 없는 타입 의미(return이 없다)



## 클래스와 객체

```java
public class FunctionTest {
    public static void main(String[] args) {
        System.out.println("테스트 시작");
        test("클래스");
        System.out.println("테스트 끝");
    }
    
    static void test(String name) { 
        System.out.println(name + "을 테스트 중입니다");
    }
}
```

- 클래스
  - 변수와 함수를 묶어서 만든 사용자 정의 자료형
  - 객체를 생성하는 틀
  - 다른 타입의 데이터들을 모으는 기능으로도 사용 가능

- 객체
  - 하나의 역할을 수행하는 메소드와 변수의 묶음

- 객체지향 프로그래밍
  - 프로그램을 수많은 객체라는 기본 단위로 나누고 상호작용 하는 방식으로 서술 하는 것




### 객체의 구성

- 속성(Attribute) - 멤버 변수
- 동작(Behavior) - 메소드

```java
class TV {
    int channel;		// 속성(Attribute)
    int volume;
    public void channelUp(){		// 메소드
        
    }
    public void channelDown(){		// 메소드
        
    }
}
TV tv = new TV();
tv.channelDown();
```



### 추상화와 클래스

- 필요한 객체를 설계해서 프로그램이 인식하게 하는 방법
  - 클래스를 설계
  - 객체 생성
  - 생성된 객체는 클래스에 정의한 속성과 동작을 가짐



### 클래스 선언

`public static void main(String [] a){}`

```java
[접근제한자] [활용제한자] class 클래스명 {
    속성 정의
    기능 정의
}
```

- 접근제한자
  - public
  - default()
  - protected
  - private
- 활용제한자
  - static
    - 클래스이름.메소드이름 으로 호출
  - final
  - abstract
  - synchronized



### 메소드

- 객체가 할 수 있는 행동 정의
- 메소드의 이름은 소문자로 시작하는것이 관례

```java
class Test{
    public void call(int val) {
        
    }
}
Test t = new Test();
t.call(100);
// static일 경우
class Test{
    public static void call(){
        
    }
}
Test t = new Test();
Test.call();
```



---

## 생성자

- 객체가 생성될때 최초 한번 수행되는 함수.
- 클래스 명과 이름이 동일
- 반환 타입이 없음

```java
public class Dog {
    Dog() {
        System.out.println("생성자")
     	System.out.println("반환 타입이 없다")
    }
}
```

### 디폴트 생성자

- 클래스 내에 생성자가 하나도 정의되어 있지 않을 경우 JVM이 자동으로 제공하는 생성자

- 매개변수가 없는 형태 `클래스 명() {}`

### 오버로딩

```java
class Dog{
    // 생성자도 함수니까 오버로딩이 가능
    Dog(){}
    Dog(String name){}
    Dog(int age){}
    Dog(String name, int age){}
}
```

- 클래스 내에 메소드 이름이 같고 매개변수의 타입 또는 개수가 다른 것

### this

- static 영역에서는 사용 불가
- 생성자 내에서만 호출이 가능
- 생성자 내에서 첫번째 구문에 위치해야함

```java
// this.멤버 변수
public class Dog{
    String name;
    int age;
    void info(){
        System.out.print(this.name);
        System.out.println(this.age);
    }
    
    Dog(String name, int age){
        this.name = name;	//this.name은 public class Dog 바로 밑의 name을 의미
        this.age = age;
    }
    
}
```

```java
// this.([값]) => 생성자 호출
class Dog{
    String name;
    int age;
    Dog(){
        this("멍멍이",3)		// Dog(String name, int age)호출, 인자는 멍멍이,3
    }
    Dog (String name, int age){
    }
}
```



### static

```java
public class StaticTest {
    static int val = 50;
	}
	public static void main(String[] args) {
        StaticTest st = new StaticTest();
        System.out.println(val)
    }

public class StaticTEst1 {
    int val = 50;
	}
	public static void main(String[] args) {
        StaticTest st = new StaticTEst();
        System.out.println(st.val)
    }
```



#### 로딩시점

- static: 클래스 로딩 시
  - 객체를 생성하지 않아도 호출 가능

- non-static: 객체 생성시

#### 메모리

- static : 클래스당 하나의 메모리 공간 할당
- non-static: 인스턴스 당 메모리를 할당

#### 문법

- static : 클래스 이름으로 접근
- non-static: 객체 생성 후 접근

```java
class Test{
    static int cnt;
    String name;
}

class Main {
    public static void main(String [] a) {
       Test account = new Test();
       account.name = "ljm";
       account.cnt ++;	//객체에서도 접근 가능
       Test.cnt ++;
       
    }
}
```

#### static => non-static 직접 접근이 불가

```java
class Main{
    String name = "lee";
    public static void main(String [] a){
        System.out.println(name); // 오류
        
        Test t = new Test();
        System.out.println(t.name)
    }
}
```

#### non-static => static접근

```java
class Main {
    static int cnt = 100;
    public void call () {
        System.out.println(cnt)
    }
}
```



---

## 접근 제한자(access modifier)

### 패키지

- 프로그렘의 클래스를 관리하기 위해 패키지 이용
- `.`(dot)을 이용하여 패키지 구분

### import

- 다른 패키지에 있는 클래스를 사용하기 위한 과정

```java
//packge_name 패키지안의 class_name이 import
import package_name.class_name;

// package_name의 모든 class가 import, package_name 바로 밑의 class만 import 됨
import package_name.*;
```

```java
package com.ljm.project.service;
import com.ljm.project.dto.Test;

public class TestService {		// TestService는 package에 들어있는 클래스
    Test t;
}
```

### 캡슐화(Encapsulation)

- 객체의 속성(data fields) & 행위(methods)를 하나로 묶음
- 실제 구현 내용 일부를 은닉 가능

```java

public class MotorBike{
  int speed;
  
}

public class MoterBikeRunner {
	public static void main(String[] args) {
		MoterBike hyundai = new MoterBike();
		MoterBike honda = new MoterBike();
		hyundai.speed = 100;  // 메서드를 거치지 않고 데이터를 외부에서 제어 => 캡슐화에 위배
		honda.speed = 80;
	}
}

// 개선
public class MotorBike{
	private int speed;
  
  void setSpeed(int speed){
    this.speed = speed;
  }
}

public class MoterBikeRunner {
	public static void main(String[] args) {
		MoterBike hyundai = new MoterBike();
		MoterBike honda = new MoterBike();
    hyundai.setSpeed(100);
    honda.setSpeed(80);
  }
}

```



### 접근 제한자

- 클래스, 멤버 변수, 멤버 메서드 등 선언부에서 접근 허용 범위를 지정하는 역할

```java
class Race{
    // int speed;
    private int speed
    public void speedUp(){
        if (speed < 200)
            speed +=10;
    }
    public int getSpeed(){
        return speed;
    }
    
    public void setSpeed(int speed){
        if (speed >=0 && speed < 200)
            this.speed = speed;
    }
}
public class CarTest {
    public static void main(String[] args) {
        Race r = new Race();
        r.speedUp();
        // r.speed = 500; private라 접근 불가
        r.setSpeed(150);
    }
}
```

#### public

- **모든 위치**에서 접근이 가능

#### protected

- **같은 패키지**에서 접근이 가능
- 상속관계일 경우엔 다른 패키지에서도 접근 가능

#### default

- **같은 패키지**에서만 접근이 허용
- 접근제한자가 선언 안 되었을 경우 기본 적용 값

#### private

- **자신 클래스**에서만 접근이 허용

#### 그외

- static : 클래스 레벨 요소 설정

- final : 요소 수정 불가
- abstract : 추상 메서드 및 추상 클래스 작성



### 싱글턴 패턴(Singleton Pattern)

- 디자인 패턴
- 생성자가 여러 차례 호출되어도 실제로 생성되는 객체는 하나
- 최초 생성 이후에 호출된 생성자는 최초의 생성자가 생성한 객체 리턴

```java
public class Manager {
    private static Manager manager = new Manager();
    private Manager(){}
    public static Manager gerManager() {
        return manager
    }
}
```

---

## 상속(Inheritance)

```java
public class Person{
    String name;
    int age;
    public Person(String name, int age){
        this.name = name;
        this.age = age;
    }
    
    public void eat() {
        System.out.println("오늘 저녁은 뭘 먹을까?")
    }
}

public class Friend extends Person {
    String nickname;
    
    public Friend(String name, int age, String nickname) {
        super(name,age) //부모클래스의 기본 생성자가 없어서 자식생성자에서 호출을 해줘야함
        this.nickname = nickname
    }
}
```

- `extends class_name`
- 부모(Super) 클래스 // 자식(Sub) 클래스
- 확장성, 재사용성
  - 부모의 생성자, 초기화 블록은 상속 되지 않음
- 부모 클래스의 멤버변수, 메소드를 접근 제한자에 따라 사용 가능
- Object  클래스는 모든 클래스의 조상 클래스
  - extends 선언이 없는 클래스는 estends Object가 생략되어 있는것

- **super** 키워드를 통해 조상 클래스의 생성자 호출 가능



### 오버라이딩(재정의, overriding)

```java
public class Friend extends Person {
    String nickname;
    
    public Student(String name, int age, String nickname){
        super(name,age);
        this.nickname = nickname;
    }
    @Override
    public void eat() {
        System.out.println("우리 오늘 저녁에 뭐먹을까?")
    }
}
```

- 상위 클래스에 선언된 메서드를 자식 클래스에서 재정의 하는것
- 메서드의 이름,반환형,매개변수 동일 해야함
- 하위 클래스의 접근 제어자 범위가 상위 클래스보다 크거나 같아야함
- **@Override**
  - override 했다는 것을 알리기 위한 용도
  - 같은 이름의 메서드가 부모 클래스에 없을 경우 에러 발생
    - 철자 오류 등 디버깅에 도움



### Object 클래스

- 가장 최상위 클래스

#### toString 메서드

- 객체를 문자열로 변경(주소 값)

```java
public String toString() {
    return getClass().getName() + "@" + Integer.toHexString(hashCode());
}
```

#### equals 메서드

- 두 객체가 같은지를 비교(주소 값 비교)

```java
// 두 객체의 주소값 비교
public boolean equals(Object obj) {
    return (this == obj);
}
```

- String 비교시에 사용

  ```java
  String a = 'ljm';
  String b = 'ljm';
  a == b; false
  a.equals(b) //true
  ```
  
  

#### hashCode

- 시스템에서 객체를 구별하기 위해 사용되는 정수값
- HashSet, HashMap등에서 객체 동일성 확인하기 위해 사용
- equals 메서드 override시 hashCode 재정의 필요

#### final

- 접근제한자의 final
- 한번 할당되고 나면 변경이 불가
- 변수를 상수로 사용할 때 사용
- 메소드 override 금지할 때 사용
- 클래스 상속을 막을 때 사용
  - String과 같이 기본 제공 클래스 막을때 등 사용



---

## 다형성(Polymorphism)

- 상속관계에 있을 때 **조상(부모)** 클래스의 타입으로 **자식 클래스 객체 참조**

```java
Person p = new Friend("ljm",27,"맛대");
Friend f = new Person("ljm",27); // 불가
```

- 다른 타입의 객체를 다루는 배열에서 사용

- 매개변수 다형성 이용

  - 메서드 호출시 메서드 이름,파라미터 맞춰야함

  - ```java
    public void println(Object x) {		// Object로 처리하여 타입에 따라 메서드 만들필요x
        String s = String.valueOf(x);
        synchronized (this) {
            print(s);
            newLine();
        }
    }
    ```

- 참조형 객체의 형 변환

  - ```java
    // 작은 범위 => 큰 범위 : 묵시적 캐스팅
    byte b = 10;
    int i = b;
    // 자손 타입의 객체 => 조상타입 변환시 형 변환 생략 가능
    Friend f = new Friend();
    Object obj = f;
    ```

  - ```java
    // 큰 범위 => 작은 범위 : 명시적 캐스팅
    int i = 10;
    byte b = (byte)i;
    
    Person p = new Friend();
    Friend f = (Friend)p
    // 이러한 경우 자손의 메서드 사용에 제한 받을 수 있음
    ```

  - `instanceof`: 실제 메모리에 있는 객체가 특정 클래스의 타입인지 boolean 값으로 return

    - ```java
      Person person = new Person();
      if (person instaceof Friend) {
          Friend friend = (Friend)person;
          friend.eat();
      }
      ```

#### 동적 바인딩

- 부모 class에 `int data = 20;` 자식 클래스에 `int data = 30'`
- `Parent test = new Child();`
  - `test.data = 20` 

- 부모 class에 `public void print(){System.out.println("부모")}`
- 자식 class에 `public void print(){System.out.println("자식")}`

- `Parent test = new Child();`
  - `test.print()` => `자식 ` 출력

- 일반적으론 해당 객체에서 찾음 (test가 Parent 객체이므로 Parent에서 찾음)
- **함수**의 경우는 오버라이딩 한 자식을 호출

## 추상클래스(abstract class)

- K_Chef & J_Chef

```java
public class K_Chef {
// public abstract class Chef {
    Sting name;
    int age;
    String speciality;
    public void eat() {
        System.out.println("음식을 먹는다")
    }
    public void cook() {
        System.out.println("한식");
    }
}

public class J_chef {
    ... K_Chef와 동일;
    public void cook() {
        System.out.println("일식")
    }
}
```

- 공통된 부분을 묶은 Chef class

```java
public class Chef {
    String name;
    int age;
    String speciality;
    
    public void eat() {
        System.out.println("음식을 먹는다");
    }
    public void cook() {		// 결국 Chef에선 쓸 일이 없으므로 내용을 지워버림
        System.out.println("음식"); 
    }
    // public abstract void cook();
}

public class K_Chef extends Chef{
    @Override
    public void cook() {
        System.out.println("한식");
    }
}
----
public class ChefTest {
    public static void main(String[] args){
        Chef[] chefs = new Chef[2];
        
        chefs[0] = new K_Chef();
        chefs[1] = new J_Chef();
        for (Chef chef : chefs) {
            chef.eat();
            chef.cook();
        }
    }
}
// 음식을 먹는다
// 한식
// 음식을 먹는다
// 일식
```

- 구현이 무의미 한 경우(Chef의 `cook()`) 선언부만 남기고 구현부를 제거
- 구현부가 없으므로 abstract 키워드를 메서드 선언부에 추가
  - 객체를 생성할 수 없는 클래스이므로 클래스 선언시에도 abstract 추가



### 특징

- 상속 전용 클래스
- 객체 생성 불가



## 인터페이스

- 완벽히 추상화된 객체 : 모든 메서드가 abstract 형태

```java
public interface InterfaceTest {
    public static final int MEMBER1 = 10;
    inf MEMBER2 = 10;
    
    public abstrat void method1(int params);
    void method2(int param);
}
```

- interface 키워드를 이용하여 선언
- 선언되는 변수는 모두 상수로 적용
- 선언되는 메소드는 모두 추상 메소드로 적용

- 객체 생성이 불가능
- 클래스가 인터페이스 상속시 `extends`가 아닌 `implements` 이용
  - `class Circle implements Shape {}`
- 인터페이스를 상속받는 하위클래스는 추상 메소드를 반드시 오버라이딩 해야함
  - 구현하지 않을 경우 abstract 클래스로 표기



### 필요성

- 표준화 처리
- 쉬운 모듈 교체
- 상속 관계가 없는 클래스들에게 인터페이스를 통한 관계 부여로 다형성 확장
- 모듈 간 독립적 프로그래밍 가능
