# JAVA intro

## JVM(자바 가상 머신)

- JAVA 바이트코드를 실행할 수 있는 주체
- 플랫폼에 독립적
  - OS에 종속받지 않고 CPU가 JAVA를 인식,실행할 수 있게 하는 가상 컴퓨터

---

### 메인 메소드

- **main()**
- java 실행 시 가장 먼저 호출되는 부분
- Application에서 main() 메소드가 없다면 실행 될 수 없음
  - Application의 시작 = 특정 클래스의 main() 실행
- `public static void main(String [] args){}`



### 주석

- `//` : 한줄 주석
- `*` : 여러줄 주석



### 출력문

```java
public abstract class print_test {
	public static void main(String[] args) {
		System.out.println("Hello World");
	}
}
```



- print

  - `System.out.print("Hello World \n");`
    - `\n` : 줄 바꿈

- println

  - 출력후 줄 바꿈 자동 처리

- printf

  - %d : 정수

    - `System.out.printf("5 * 2 = %d", 5*2).println()`

    - `System.out.printf("%d * %d = %d", 5, 7, 5 * 7).println()`

  - %f : 실수

  - %c : 문자

  - %s : 문자열

  - ```java
    System.out.printf("%d \n",10); //정수 (10진수)
    System.out.printf("%o \n",10); //정수 (8진수), 결과값 12
    System.out.printf("%x \n",16); //정수 (16진수), 결과값 10
    
    System.out.printf("%4d \n",10); // 4칸 확보 후 오른쪽부터 차지
    System.out.printf("%-4d \n",10); // 4칸 확보 후 왼쪽부터 차지
    System.out.printf("%04d \n",10); // 4칸 확보 후 오른쪽부터 차지(빈공간은 0)
    
    System.out.printf("%.2f \n",10.1); // 실수,소수점 둘쨰 자리 까지
    
    System.out.printf("%s는 시험에서 %d점을 맞았다.","ljm",95);
    ```

- `"` 출력 원할시 `System.out.print("\"")`



### 변수

```java
int a;
a = 50;
System.out.println(a);
```



- 데이터를 저장할 메모리의 위치를 나타내는 이름
- 메모리 상에 데이터를 보관할 수 있는 공간을 확보
- 적절한 메모리 공간 확보를 위해 변수의 타입이 생김
- `=` 을 통해서 CPU에 연산작업 의뢰



#### 메모리 단위

- 0과 1을 표현하는 bit
- 8bit = 1byte



#### 선언

- `자료형 변수명;`
  - int num;
  - String name;

#### 초기화

- `변수명 = 저장할 값;`
  - num = 0850;
  - name = 'ljm'

#### 선언 + 초기화

- `자료형 변수명 = 저장할 값;`
  - int num = 0850;



#### 특징

- 대소문자를 구분
- 공백은 허용x
- 숫자로 시작 불가
- `$`와 `_`를 변수 이름에 사용 가능
- 예약어(keyword)를 변수명으로 지정 불가



---

### 이클립스 단축키

- `ctrl + shift + F` : 정렬
- `ctrl + shift + C`: 여러줄 주석
