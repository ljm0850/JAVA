# 예외처리

## Error & Exception

### Error

- 메모리부족, stack overflow 등 발생시 복구 할 수 없는 상황
- 프로그램의 비 정상적 종료를 막을 수 없음

### Exception

- 프로그램 코드에 의해 수습될 수 있는 상황
  - 예외 감지 및 예외 발생 시 동작할 코드 작성 필요



### 예외 클래스의 계층

- Checked exception 계열
  - 예외에 대한 대처 코드가 없으면 컴파일이 진행되지 않음
- Unchecked exception (RuntimeException의 하위 클래스)
  - 예외에 대한 대처 코드가 없어도 컴파일은 진행



### 키워드

#### 예외 직접 처리

- try
- catch
- finally (예외 발생 여부 상관 없이 언제나 실행)
  - 중간에 return을 만나도 finally 블록 수행 후 retrun

```java
try {
    // 예외 가능성이 있는 코드
} catch (Exception e) {
    // 예외 발생시 처리할 코드
}
```

- catch를 여러번 사용하여 `(Exception e)` => `(XXException e)` 변환하여 해당 예외 발생시 처리 가능



#### 간접 처리

- throws
- method에서 처리해야 할 예외를 호출한 곳으로 전달
  - 예외가 없어지는 것이 아님

```java
void exceptionMethod() throws Exception1, Exception2 {
    // 예외 발생 코드
}

void methodCaller() {
    try{
        exceptionMethod();
    } catch(Exception e){}
}
```



#### 사용자 정의 예외처리

- throw



#### Throwable 메서드

- `public String getMessage()` : 발생된 예외에 대한 구체적인 메세지를 반환
- `public Throwable getCause()` : 예외의 원인이 되는 Throwable 객체 또는 null 반환
- `public void printStack Trace()` : 예외가 발생된 메서드가 호출되기까지의 메서드 호출 스택을 출력



#### checked exception & throws

```java
public static void main(String[] args) {
    CheckedThrowsTest et = new CheckedThrowsTest();
    try {
        et.method1();
    } catch (ClassNotFoundException e) {
        System.out.printf("exception : %s%n",e.getMessage());
    }
    System.out.println("exit")
}
public void method1() throws ClassNotFoundException {
    method2();
}
public void method2() throws ClassNotFoundException {
    Class.forName("Some Class")		// ClassNotFoundException 발생
}
```

- try~ catch 또는 throws 필요
- 필요한 곳에서 try~catch 처리

#### runtime exception & throws

```java
public static void main(String[] args) {
    RuntimeThrowTest et = new RuntimeThrowsTest();
    try {
        et.method1();
    } catch (ArithmeticException e) {
        System.out.printf("예외 처리: %s%n",e.getMessage());
    }
    System.out.println("exit")
}
public void method1() {
    method2();
}
public void method2() {
    int i = 1/0;		// ArithmeticException 발생
}
```

- throws 하지 않아도 전달 되지만, 결국 try~catch 처리



#### 사용자 정의 예외

- API에 정의된 exception 이외에 필요에 따라 사용자 정의 예외 클래스 작성
- 대부분 Exception 또는 RuntimeException 클래스를 상속 받아 작성
  - checked exception 활용 : 명시적 예외 처리 또는 throws 필요
    - 코드는 복잡해지지만 처리 누락 등 발생 가능성이 낮음
  - runtime exception 활용 : 묵시적 예외 처리 가능

```java
public class UserExceptionTest {
    private static String[] fruits = {"사과","귤","포도"};
    public static void main(String[] args) {
        boolean result = getFruit1("사과");
        if(!result) {
            System.out.println("사과가 없다");
        }
        result = getFruit1("사과");
        if(!result) {
            System.out.println("사과가 없다");
        }
        System.out.println("창고 정리 끝")
    }
    private static boolean getFruit1(String name) {
        for (int i=0; i< fruits.length; i++) {
            if (fruits[i] != null && fruits[i].equals(name)) {
                fruits[i] = null;
                return true;
            }
        }
        return false;
    }
}

```

```java
class FruitNotFoundException extends Exception {
    public FruitNotFoundException(String name) {
        super(name + "에 해당하는 과일이 없습니다");
    }
}
public class CustomExceptionTest {
    private state Sting[] fruits = {"사과","귤","포도"};
    public static void main(String[] args) {
        try{
            getFruit2("귤");
            getFruit2("귤");
        } catch (FruitNotFoundException e) {
            e.printStackTrace();
        }
    }
    
    private static void getFruit2(String name) throws FruitNotFoundException {
        for (int i = 0; i < fruits.length; i++) {
            if (fruits[i] != null && fruits[i].equals(name)) {
                fruits[i] = null;
                return;
            }
        }
        throw new FruitNotFoundException(name);
    }
}
```

