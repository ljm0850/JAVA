# Method

```java
void sayHelloWorld(){
  System.out.println("Hello World");
}
```

- void : return값이 없으므로 void
- Method의 이름은 변수명과 같은 규칙을 적용받음
  - 숫자로 시작 불가 ect...

## 기본 구조

```java
ReturnType nameOfTheMethod (Type argumentName) {
  // 실행할 내용
}
```

```java
void sayHelloWorld(int numOfTimes){
  for (int i = 0; i< numOfTimes; i++){
    System.out.println("Hello World");
  }
}
```



### 오버로딩

```java
void sayHelloWorld(){
  System.out.println("Hello World");
}

void sayHelloWorld(int numOfTimes){
  for (int i = 0; i< numOfTimes; i++){
    System.out.println("Hello World");
  }
}

void sayHelloWorld(String str){
  System.out.printf("Hello World %s",str).println();
}
```

- 같은 변수명이지만, parameter에 따라 다른 메서드를 호출

#### 가변인자

```java
public static int calculateSum(int... numbers) {
        int sum = 0;
        for (int num : numbers) {
            sum += num;
        }
        return sum;
}
```

- parameter의 수가 일정하지 않을 때 사용
- 이 때 numbers의 타입은 배열 (int[] numbers)



