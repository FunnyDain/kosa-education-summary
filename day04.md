## 데이터 타입과 메모리

<br>

> 데이터 타입
> 
<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https://t1.daumcdn.net/cfile/tistory/21321F34586F19FD07"/>

- 기본 타입 + 참조타입
- 기본 타입으로 선언된 변수는 값 자체를 저장
- 참조 타입으로 선언된 변수는 객체가 생성된 메모리번지를 저장
- 메모리 상 변수들의 값
    
<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https://t1.daumcdn.net/cfile/tistory/25776B3D586F1B3816"/>
    
    - 변수들은 모두 스택메모리 영역에 생성
    - 참조변수는 힙 메모리 영역의 String객체 번지를 저장하고,
    이 번지를 통해 String객체를 참조

> 메모리 사용 영역
> 
<img src="https://user-images.githubusercontent.com/42092864/161595316-4a99d9cc-ba06-4b84-bd97-40fdde983139.png"/>

- java 명령어 ⇒ JVM구동 ⇒ JVM 운영체제에서 할당받은 메모리 영역을(Runtime Data Area)을 다음과 같이 구분하여 사용
- 메소드 영역(Method Area)
    - 바이트코드 파일의 내용이 저장되는 영역
    - 클래스별로 상수, 정적 필드, 메소드 코드, 생성자 코드 등이 저장
- 힙 영역(Heap Area)
    - 객체가 생성되는 영역
    - 객체의 번지는 메소드영역과 스택영역의 상수와 변수에서 참조할 수 있다.
- 스택 영역(Stack Area)
    - 메소드가 호출할 때마다 생성되는 프레임이 저장되는 영역
    - 메소드 호출이 끝나면 프레임이 자동 제거
    - 프레임 내부에는 로컬 변수 스택이 있다.
    - 여기에서 기본타입 변수와 참조 ㅂ타입 변수가 생성되고 제거

> 참조 타입 변수의 ==, !=
> 
- 값이 아닌 객체의 번지를 비교
- 번지가 같다면 동일한 객체를 참조하는 것

> 객체를 제거하는 법 : null
> 

```java
String hobby = "여행";
hobby = null;   //"여행"에 해당하는 String 객체를 쓰레기로 만듬 => garbage collector를 실행시켜 자동으로 제거

String kind1 = "자동차";
String kind2 = kind1;   //kind1 변수에 저장되어 있는 번지를 kind2변수에 대임
kind1 = null;   //"자동차"에 해당하는 String객체는 쓰레기가 아님, kind2가 참조하고 있기 때문
```
<br>

---
<br>

## String 문자열

> 문자열 비교
> 

```java
String name1 = "홍길동";
String name2 = "홍길동";

=> name1과 name2는 스택메모리에서 같은 객체주소를 가진다. ex) 10

//new 연산자를 사용
String name3 = new String("홍길동");
String name4 = new String("홍길동");
=> name1과 name3는 스택메모리에서 다른 객체주소를 가진다.
=> name3과 name4는 스택메모리에서 다른 객체주소를 가진다.
```

- 내부 문자열만을 비교 할때는 == 가 아니 **equals()사용**
    
    ```java
    name3.equals(name4);        => true
    ```
    

> 문자 추출
> 
- 특정 위치 문자를 얻고 싶다면 **charAt(인덱스)**

> 문자열 길이
> 
- 문자의 갯수 **length()**

> 문자열 대체
> 
- **replace()**
- 자바 문자열은 불변, 수정본이 아니라 완전히 새로운 문자열

```java
String oldStr = "자바 프로그래밍";
String newStr = oldStr.replace("자바","JAVA");
```

> 문자열 잘라내기
> 

| 메소드 | 설명 |
| --- | --- |
| substring(int beginIndex) | beginIndex에서 끝까지 잘라내기 |
| substring(int beginIndex, int endIndex) | beginIndex에서 endIndex앞까지 잘라내기 |

```java
String ssn = "880815-1234567";
String firstNum = ssn.substring(0,6);
String secondNum = ssn.substring(7);
```

> 문자열 찾기
> 
- **indexOf()**

```java
String subject = "자바 프로그래밍";
int index = subject.indexOf("프로그래밍");   //3

//주어진 문자열이 포함되어 있지 않으면 -1을 리턴
if(index == -1){

}else{

}
```

> 문자열 분리
> 
- 구분자를 사용하여 여러개의 문자열로 구성되어 있을 경우
- **split()**

```java
String board = "번호, 제목, 내용, 성명";
String[] arr = board.split(",");
```
<br>

---
<br>

## 배열

- 많은 양의 데이터를 다루어야 할 때
- 처리할 데이터의 타입 ⇒ 처리할 데이터의 갯수 ⇒ 배열크기
- 객체로 취급됨

> 배열의 생성 방법
> 

(1) 크기 : new 타입[크기]

```java
//한번 정해진 배열 크기를 조절 할 수 없음
new int[10], new boolean[5], new char[28]
```

(2) 값 : {값1, 값2, 값2, …}, new 타입[]{값1, 값2, 값2, …}

```java
{1,2,3,4,5},{'a','b','c'}
new int[]{1,2,3,4,5}, new char[]{'a','b','c'}
```

> 배열 변수 선언 방법
> 

: 타입[] 변수명;

```java
int[] nums;
char[] characters;
```

> 배열의 사용 방법
> 

```java
int[] nums = new int[10];
nums.length       //길이, 10
nums[숫자인덱스]

0~nums.length-1
```

> [I@7d6f77cc : 객체 번지
> 
- @앞 객체 타입
- @뒤 참조값

> 2차원 배열의 생성
> 

```java
new 타입[행의 크기][열의 크기]
		{{첫번째 행의 데이터들},{두번째 행의 데이터들},{세번째 행의 데이터들}}
new 타입[행의크기][]

//2차원 배열 변수
타입[][] 변수명;
타입 변수명[][];
타입[] 변수명[];

int[][] numArr = new int[3][4];

int[][] score = {
				{100, 100, 100},
				{20, 20, 20},
				{30, 30, 30},
				{40, 40, 40},
				{50, 50, 50},
		};
		
int[][] score2 = new int[5][3];

for (int i = 0; i < score2.length; i++) {
	for (int k = 0; k < score2[i].length; k++) {
		score[i][k] = 10;
	}
}

```

---

> .java 와 .class
> 

```java
xxx.java   --- javac --->  xxx.class  --- java ---> 
```

- javac : 컴파일 명령어
    - 저장하면 .class파일로 생성됨
    - src - .java파일(자바파일)
    - bin - .class(실행파일)
- JVM(Java Virtual Machine)가 OS운영체제 위로 올라감, 운영체제마다 다름(jdk다르게 설치하는 이유)
- java : 바이너리 코드로 실행되는 명령어

<br>

---
<br>

## 열거(Enum)타입

- 데이터 중 몇가지 한정되는 값
    
    ```java
    ex) 요일 월~일 => 7개
        계절 봄~겨울 => 4가지
    ```
    

```java
Week.java

public enum Week{
	
	//열거 상수 목록
	MONDAY,
	TUESDAY,
	WEDNESDAY,
	THURSDAY,
	FRIDAY,
	SATURDAY,
	SUNDAY
}

//관례적으로 알파벳, 대문자, _로 연결

//열거 타입 변수에 열거 상수 대입
Week today = Week.SUNDAY;

//열거 상수 비교는 ==, != 연산자 사용
tody == Week.SUNDAY;   //결과: true\
```