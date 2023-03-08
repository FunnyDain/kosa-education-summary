# 00. 깃허브에 소스관리

<br>

> 외부 앱에서 로그인 시 사용하는 토큰 생성 과정
> 

[[GitHub] 깃허브 토큰(Token) 생성하는 법](https://hoohaha.tistory.com/37)

- workflow부터 전체 선택
- 토큰
    
    <aside>
    💡 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
    
    </aside>
    

> 이클립스의 자바 프로젝트를 깃 허브의 리파지토리와 동기화 하기
> 

💯소스관리 **날짜별** or 내용별

day01 , day02…

- Window - Show view - Other - Git - Git Repositories
- 원격 저장소 생성
    - repository - Remote - Create Remote
        
- 로컬 저장소 commit & 원격에 push
  - 프로젝트 우클릭 - Team - Commit and push
        


<br> 
<br>

# 01. 자바 시작하기
<br>

## 이클립스 setting

- C:\kosastudy\workspace workspace
- Preference - Workspace - Other - utf -8
    
    💫 ms949 vs utf -8
    
    - 컴퓨터는 문자(영문 or 한글) 사용할 수 있게 코드값이 정해져 있다.
        
        
        | 영문 | 한글 |
        | --- | --- |
        | 196x | 1987 (표준한글코드) |
        | ASCII or
        8859-1 | KSC5601
        (외국에서는 EUC-KR, MS949(CP949)) |
        | 1바이트
        0x00~0x7F
        (A : 0x41) | 2바이트
        (가 : 0xB0A1) |
        
        ⇒ Unicode(유니코드) 등장
        
    - UTF-16 : 영문이든 한글이든 2바이트(16비트), 모든 언어를 지원x , 2의 16승까지이기 떄문- 자바
    - **UTF-8** : 1바이트 ~ 4바이트, 한글은 3바이트(아시아는 통일됨)
        
        ⇒ **웹에서는 표준**
        
- jdk 11
    - Preference - Installed JREs - Standard VM -11
        
    - Preference - Compiler - 11
    
<br>

---
<br>

## 프로젝트 생성

- New - Other - Java Project
    - name : javaedu
    - jre - jdk 11
    

> 맛보기 class 생성
> 
- FirstApp.class
    
    ⚠️ 이클립스 오류 - Requesting JavaScript AST from selectionerror라는 JSDT 버그 발생시,
    
    Mark Occurrences 에서 'Mark occurrences of the selected element in the current file.’ 체크박스 해제
    
    ⚠️ Help - About Eclipse IDE - Installed Details - Spring으로 시작하는 plugin 모두 삭제(Uninstall)
    

> 주석
> 

| 단축키 | 설명 |
| --- | --- |
| Ctrl + / | // , 단일 주석 |
| Ctrl + Shift + / | /* */, 블럭주석 |

<br>

---
<br>

## cmd 컴파일 & 실행

> 컴파일
> 

```java
javac -d [바이트코드파일저장위치][소스경로/*.java]
javac -d bin src/ch01/sec06/Hello.java

=> 결과
temp/bin 디렉토리에 바이트코드 파일(ch01/sec06/Hello.class)이 생성
```

> 실행
> 

```java
java -cp [바이트코드파일위치][패키지...클래스명]
java -cp bin ch01.sec06.Hello

=> 결과
콘솔에 Hello.Java가 출력

```

<br> 
<br>

# 02. 변수와 타입

## 타입

> **리터럴(literal)**
> 
- 프로그램에서 작성되는 데이터 값(value) 작성 방법에 따라서 인식되는 타입이 달라진다.

```java
1(int), 1.0(double), 1L(long), ‘1’(char), “1”(String)

1 + 1 --> 2
1.0 + 1 --> 2.0
'1' + 1 --> 50        //'1'는 char타입 => 10진수로 49이다. 49 + 1 = 50
"1" + 1 -> "11"
```

- 고정된 값

> 타입
> 

| 타입 | 종류 |
| --- | --- |
| 정수형 | int(10), long(10L) |
| 실수 | float(3.14f), double(3.14) |
| 문자형 | ' ’, ‘a’, ‘1’, ‘가’, ’%’, ‘:’, ‘\n’(줄 바꿈), ‘\t’(tap) |
| 논리형 | true, false |
| 문자열형 | "”, “100”, “가나다”, “abc”, “3”, “가” |
| 객체형(참조형) | null (0과 다름, 값이 없는 것이 아니라 참조하는 것이 없는 것),  |

<br>

---
<br>

## 변수

- 연산 결과 값 or 리터럴을 보관하는 메모리상의 방
- 필요할 때 생성하여 사용
- 변수를 생성 —> **변수 선언**

> 생성 방법
> 

```java
**타입 변수명;**              //방이 정해짐
**타입 변수명 = 값;**

// 선언
**int total;
double avg;
char grade;**

//변수에 최초로 값을 할당 : 초기화
**int total = 100;
double avg = 1.0;
char grade = 'A';**          

//할당, 대입
total = 1000;              
//변수 = 식
//l-value(방,장소) = r-value(값) : 변수, 리터럴, 연산식, 리턴값이 있는 메서드의 호출식

//주의
char munja = 'A';  
System.out.print(munja);		//A
munja++;
System.out.print(munja); 		//B
munja += 1;
System.out.print(munja); 		//C
//munja = (munja+1); 			//error
munja = (char)(munja+1); 
System.out.println(munja);  	//D
```

1. 변수에 저장할 값의 용도 —> 변수명
2. 변수에 저장할 값의 종류 —> 타입

⚠️ total = 3.14 error, total은 타입이 int이기 때문에 강제 형변환하지 않는 이상 이렇게 쓸 수 없다.

> 어떤 값을 표준출력장치(화면)로 출력하는 방법
> 

```java
**System.out.println();
System.out.print();
System.out.printf();**
```
<br>

---
<br>

## 타입별 크기비교

- 크기 : 저장할 수 있는 값의 범위
- double > float > long > int > short > byte
- double > float > long > int > char

<aside>
💡 크기가 큰 것을 작은 값으로 넣을 수 없다. (작은 것에서 큰 것은 가능)
그래서 int를 char로 바꾸고 싶다면 강제형변환해줘야함

</aside>
<br>

> 문자열 타입변환
> 

| 변환타입 | 사용 예 |
| --- | --- |
| String → byte | String str = “10”
byte value = Byte.parseByte(str); |
| String → short | String str = “200”
short value = Short.parseShort(str); |
| String → int | String str = “300000”
int value = Integer.parseInt(str); |
| String → long | String str = “40000000000”
long value = Long.parseLong(str); |
| String → float | String str = “12.345”
float value = Float.parseFloat(str); |
| String → double | String str = “12.345”
double value = Double.parseDouble(str); |
| String → boolean | String str = “true”
boolean value = Boolean.parseBoolean(str); |
| 기본타입 → String  | String str = String.valueOf(기본타입값)                                                                                       |
<br>

---
<br>

## 콘솔로 변수값 출력

: println(내용), print(내용), prinf(”형식문자열”, 값1, 값2, …”);

> printf() 형식문자열
> 

```java
prinf("형식문자열", 값1, 값2, …);

// 값1, 값2, ... : 형식 문자열에 제공될 값

int value = 123;

```

| 형식화된 문자열 | 설명 |
| --- | --- |
| %d, 
%6d,
-6%, 
%06 | 정수(10진수), 
6자리정수로 왼쪽 공백, 
6자리정수로 오른쪽 공백, 
6자리 정수로 왼쪽 공백 0채움 |
| %o
%x | 정수(8진수)
정수(16진수) |
| %10.2f | 실수/ 정수7자리+소수점,왼쪽빈자리공백 |
| %c | 문자형 |
| %s | 문자열 |
| \t | 탭 |
| \n | 줄바꿈 |
| %% | % |

```java
package day3;
public class PrintfTest {
	public static void main(String[] args) {
		System.out.printf("테스트입니당%n");	
		System.out.printf("테스트%d입니당\n",10);		
		System.out.printf("테스트입니당%n");
		System.out.printf("%d %x %o %c\n", 100, 100, 100, 100);
		System.out.printf("%d %1$x %1$o %1$c\n", 100);			//1$ : 100을 똑같이 줌
		System.out.printf("0x%X 0x%x\n",(int)'가',(int)'각');		//%X : 대문자, %x: 소문자, (int)안주면 error : 정수형에 특화됐기에
		System.out.printf("%c %c %c %c\n", '가', 'A', '!', '3');
		System.out.printf("%b\n", true);	//%b : boolean
		System.out.printf("%f %e\n", 100.0, 100.0);
		System.out.printf("%.2f\n", 123.5678);		//기본적으로 반올림이 적용된다.
		System.out.printf("|%s|\n", "자바");
		System.out.printf("|%10s|\n", "자바");		//| : 파이프 기호, 오른쪽 정렬, 10글자
		System.out.printf("|%-10s|\n", "자바");		//왼쪽 정렬, 10글자
		System.out.printf("%,d원\n", 1000000);		//1000단위마다 ,	
	}
}
```

<br>
<br>


# 03. 자바의 연산자
<br>

> **기능**
> 

: 산술연산자, 비교연산자, 논리연산자, 비트연산자, 조건연산자, 대입연산자(복합대입), 형변환 연산자

> 피연산자(항)의 갯수
> 

: 단항연산자, 이항연산자, 삼항연산자

```java
//단항 연산자
+, -, (타입), !, ++, --

//이항 연산자
*, /, %
+, -
>, <, >=, <=, ==, !=, instanceof
&&
||

//3항 연산자
항1 ? 항2 : 항3
=, +=, -=, *=, /=, %=, ...
```
<br> 

---
<br>

> **Math.random();**
> 

: 난수를 추출해주는 메서드, 0.0 <= ? <1.0

> 자바의 산술 이항 연산
> 

(1) int타입보다 작은 타입(char, short, byte)은 int타입으로 변환되어 연산 수행

(2) 두 항의 타입이 다를 때는 값이 손실되지 않는 범위내에서 하나의 타입으로 일치시켜서 연산 수행

⚠️ 주의

```java
char + char ---> int
short + short ---> int
byte + byte ---> int
char + long ---> long
int + long ---> long
**long + float ---> float      //float가 더 크다**
double + float ---> double

(예외 : boolean타입)
```

<aside>
💡 l-value = r-value
l-value > r-value       ⇒ 자동형변환
l-value < r-value       ⇒ 강제형변환(연산자를 이용해서), l-value = (l-value의 타입)r-value

</aside>

<br>

---
<br>
                  

> 증감 연산자
> 
- ++(1증가), —(1감소)
- 단항 연산자(전위형-앞, 후위형-뒤)
- 리터럴(값)은 항으로 사용 불가, 변수에 사용가능
- ++num, num++, —num, num—

```java
//같은 의미
++num;
num++;

//다른 의미
int result1 = ++num;   //먼저
int result2 = num++;   //나중에

System.out.println(num);      //100
System.out.println(++num);    //101 증가하고 전달
System.out.println(num++);    //100 전달하고 증가 => 101

```
<br>

---
<br>

> 조건 연산자(3항 연산자)
> 

```java
**조건식(연산 결과가 boolean타입인식) ? 참일때 수행할 식 : 거짓일때 수행할 식**

```