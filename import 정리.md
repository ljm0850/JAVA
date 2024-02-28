# import 정리

### `import java.util.Scanner;`

- input값을 받을 때 사용

- `Scanner 객체이름 = new Scanner(System.in);`
  - `in.nextByte()` : byte 형 입력 및 리턴
  - `in.nextShort()` : short형 입력 및 리턴
  - `in.nextInt()` : int 형 입력 및 리턴
  - `in.nextLong()` : long 형 입력 및 리턴

  - `in.nextFloat()` : float 형 입력 및 리턴
  - `in.nextDouble()` : double 형 입력 및 리턴
  - `in.nextBoolean()` : boolean 형 입력 및 리턴
  - `in.next()` : String 형 입력 및 리턴(공백 기준)
  - `in.nextLine()` : String 형 입력 및 리턴 (개행 기준)

```java
import java.util.Scanner;

public class ScanTest {
	public static void main(String args[]) {
		Scanner scanner = new Scanner(System.in);
		System.out.println("숫자를 입력해 주세요 : ");
		int number1 = scanner.nextInt();
		System.out.println("입력된 숫자는 " + number1);
	}
}
```



### `java.util.StringTokenizer`

- 문자열을 지정한 구분자로 쪼개주는 클래스
- 쪼개진 문자열을 Token이라 부름

```java
StringTokenizer st = new StringTokenizer(문자열);
// 띄어쓰기 기준 문자열을 분리
StringTokenizer st = new StringTokenizer(문자열,구분자);
// 구분자 기준으로 문자열을 분리
StringTokenizer st = new StringTokenizer(문자열,구분자,true/false);
// true의 경우 구분자를 문자열 토큰에 포함, default 값은 false
```

```java
import java.util.StringTokenizer;
public class Main {
  public static void main(String[] args) {
    String ljm = "ljm 0850 github";
    StringTokenizer st = new StringTokenizer(ljm);

    System.out.println(st.nextToken());
    System.out.println(st.nextToken());
    System.out.println(st.nextToken());
  }
}
// ljm
// 0850
// github
```



### `java.io.BufferedReader` (& BufferWriter)

- 버퍼를 이용하여 읽고 쓰는 함수
  - 한번 입력하면 바로 전달 => 모아서 한번에 전달
- `\n`(엔터)를 구분으로 값을 읽음



- 추후 추가 예정... 오늘 너무 피곤