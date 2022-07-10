# Generics

- 다양한 타입의 객체를 다루는 메서드
  - 미리 사용할 타입을 명시해서 형 변환을 하지 않아도 됨
  - 객체의 타입에 대한 안전성 향상 및 형상 변환 번거로움 감소



### 표현

- 클래스 또는 인터페이스 선언 시 `<>`에 타입 파라미터 표시
- `ClassName: Raw Type`
- `ClassName<T> : Generic Type`

```java
public class Classs_Name<T>{}
public interface Interface_Name<T>{}
```

- T : reference Type

- E : Element
- K : Key
- V : Value



### 객체생성

- 변수 쪽과 생성 쪽의 타입은 같아야함

```java
Class_Name<String> generic = new Class_Name<String>();
Class_Name<String> generic2 = new Class_Name<>();
Class_Name generic3 = new Class_Name(); // 문제발생
```



### 클래스 생성

```java
class NormalBox{
    private Object some;
    
    public Object getSome() {
        return some;
    }
    
    public void setSome(Object some) {
        this.some = some;
    }
}
```

```java
class GenericBox<T> {
    private T some;
    
    public T getSome() {
        return some;
    }
    
    public void setSome(T some) {
        this.some = some;
    }
}
```

### 사용

- Object를 파라미터로 사용 => 어떤 객체든 수용 가능

```java
public class NormalBoxTest {
    
    public static void main(String[] args) {
        NormalBox nBox1 = new NormalBox();
        nBox1.setSome("Hello");
        nBox1.setSome(new Toy());
        
        Object some = nBox1.getSome();
        
        if(some instanceof Toy) {
            Toy toy = (Toy)some;
        } else if(some instanceof Grocery) {
            Grocery grocery = (Grocery)some;
        } else {
            System.out.println("알수 없음");
        }
    }
}
```



- T로 객체를 한정, T의 자식까지 허용

```java
public class GenericBoxTest {
    
    public static void main(String[] args) {
        GenericBox<Toy2> gBox1 = new GenericBox<>();
        
        gBox1.setSome(new Toy2());
        
        Toy2 toy = gBox1.getSome();
        
        GenericBox<Grocery2> gBox2 = new GenericBox<>();
        gBox2.setSome(new Grocery2());
        Grocery2 grocery = gBox2.getSome();
    }
}
```



### Type parameter의 제한

- 필요에 따라 구체적인 타입 제한 필요
- 계산기 프로그렘 구현 시 Number 이하의 타입(Byte, Short, Integer)로만 제한
- type parameter 선언 뒤 extends와 함께 상위 타입 명시

```java
class NumberBox<T extends Number> {	//Number 이하의 타입 Byte,Short,Integer... 제한
    
}
```

- 인터페이스 제한하고 싶을 때도 extends로 사용
- 클래스와 함께 인터페이스 제한시 &로 연결
  - `class TypeRestrict<T extends Number & Cloneable & Comparable<String>>{}`



### Generic Type 객체를 할당 받을 때 와일드 카드 이용`

- `Generic type<?>` : 타입에 제한이 없음
- `Generic type<? extends T>` : T or  T를 상속받은 타입 사용 가능
- `Generic type<? super T>` : T or T의 조상 타입만 사용 가능



### Generic Method

- 파라미터와 리턴타입으로 type parameter를 갖는 메서드
- 메서드 리턴 타입 앞에 타입 파라미터 변수 선언

```java
[제한자] <타입_파라미터,[...]> 리턴_타입 메서드_이름(파라미터){
    // something
}
```

