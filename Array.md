# Array

## 배열

- `[]`

  - 다차원 배열 선언: `[][]`

  - ```java
    int prime [][]
    int [][] prime1
    ```

- 같은 종류의 데이터를 저장하기 위한 자료구조

- 크기가 고정되어 있음(크기 변경 불가)

- 객체로 취급

- 색인(index)를 이용하여 참조

  

### 배열의 선언

- iArr : `int [] iArr;`
- cArr : `char [] cArr;`

- bArr: `boolean [] bArr;`
- strArr: `String [] strArr;`
- dateArr: `Date [] dateArr;`



### 배열의 생성

- 1차원

  - ```java
    배열 이름 = new 배열유형 [배열크기];
    prime = new int [10]
    ```

- 2차원

  - ```java
    배열 이름 = new 배열유형[1차원배열개수][1차원배열의크기];
    prime = new int [3][2];
    prime = new int [3][];
    ```



### 자동 초기화

- 배열이 생성되면 자동적으로 배열 요소들이 기본값으로 초기화됨
  - int : `0`
  - boolean : `false`
  - char : `\u000`
  - 참조형 : `null`

```java
new int[3][2];
// [[0,0],[0,0],[0,0]]
new int[3][];
// [null,null,null]
```



### 초기화

```java
prime[0] = 100;
Arr[0][1] = 100;
```

- 인덱스는 0부터 시작
- 배열의 크기 : `배열이름.length`

```java
// {} 사용하려면 선언시에 설정해야함
int [] prime = {1,2,3};
int [][] arr = {{1,2},{3,4},{5,6}}
```



### 배열 관련 제공 API

#### System.arraycopy(src,srcPos,dest,destPos,length)

- `src` : 원본배열
- `srcPos` : 원본배열의 복사 시작 위치 (0부터 시작)
- `dest` : 복사할 배열
- `destPos` : 복사 받을 시작 위치
- `length` : 복사할 크기

```java
String [] Arr1 = {"l","j","m"};
String [] Arr2 = new String[Arr1.length +1];
System.arraycopy(Arr1,0,Arr2,0,Arr1.length);
Arr2[3] = "0850";
for (int i=0; i<destArr.length; i++)
    System.out.println(Arr2[i]);
```



#### Arrays.toString(배열객체)

- 배열안의 요소를 [item1,item2,..] 형태로 출력

```java
for (int i=0; i<arr1.length; i++)
    System.out.println(arr1[i]);
System.out.println(Arrays.toString(arr1))
```



### for-each

- 가독성이 개선된 반복문
- 배열 및 Collections에서 사용
- index 대신 elements에 접근하는 변수 제공

```java
//for-each
int intArray [] = {1,3,5,7,9}
for (int x : intArray) {
    System.out.println(x);
}
// 기존 반복문
for (int i=0; i<intArray.length; i++){
    int x = intArray[i];
    System.out.println(x);
}
```

```java
int[] intArray = {0,8,5,10,15,11,25}
int min = Integer.MAX_VALUE;
int max = Integer.MIN_VALUE;

for (int num: intArray){
    min = Math.min(min,num);
    max = Math.max(max,num);
}
System.out.printf("min: %d, max: %d%n",min,max);
```

