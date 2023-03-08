# 04. 조건문과 제어문

<br>

> 조건 연산자(3항 연산자)
> 

<aside>
💡 조건식(연산 결과가 boolean타입인식) ? 참 : 거짓

</aside>

<br>

## 조건문

```java
if(조건문)
	수행문

if(조건문)
	수행문1
else
	수행문2

if(조건식1)
	수행문1
else if(조건식2)
	수행문2
else if(조건식3)
	수행문3
	...
else
	수행문n

```
<br>

---
<br>

## switch문

- 식 : int(byte, short, char), String, enum
    
    ```java
    switch(식){
    	case 비교값1 : 수행문장1;
    								break;
    	case 비교값2 : 수행문장2;
    								 수행문장3;
    								break;
    	case 비교값3 : 수행문자4;
    								break;
    	//default생략
    	default : 수행문장5;
    						수행문장6;
    }
    ```
    
- case여러개 + 수행문장1
    
    ```java
    switch(month) {
    			case 12: case 1: case 2 :
    				System.out.println(month + "월은 겨울");
    				break;
    			case 3:
    			case 4:
    			case 5 :
    				System.out.println(month + "월은 봄");
    				break;
    			case 6:
    			case 7:
    			case 8 :
    				System.out.println(month + "월은 여름");
    				break;
    			default:
    				System.out.println(month + "월은 가을");
    ```
    
<br>

---
<br>

## 자바의 제어문

- 조건제어문(선택제어문) : if, switch
- 반복제어문 : for, while, do~while(JDBC)
- 분기제어문 : break(switch, 반복문), continue(반복문안에서만 사용가능);

<br>

---
<br>

## for와 while

> for
> 
- 반복횟수를 이미 알고 있을 때
- 배열이나 컬렉션과 같은 데이터들의 묶음으로 반복

> while
> 
- 어떠한 조건이 만족되는 동안 반복
- 무한루프

> 자바의 for문 : 2가지
> 
- for문
    
    ```java
    for(초기식; 조건식; 증감식;){
    		반복 수행 문장;
    }
    
    for(int su=1; su<=10; su++){
    		result += su;
    }
    
    //무한루프
    for(;;){
    	수행할문장
    }
    while(true){
    	수행할문장
    }
    ```
    

- foreach문
    
    ```java
    //java 5등장
    for(변수선언 : 배열 or 컬렉션객체)
    	배열이나 컬렉션 객체가 가지고 있는 데이터 값들에 대한 반복수행문장
    
    ```

⚠️ 논리연산자와 비트연산자

- 논리연산자 : &&, ||
    - 이항연산자로서 피연산자가 boolean타입이어야함
    - && : 앞의 피연산자가 false라면 뒤의 피연산자를 평가하지 않고 false를 산출
    - || : 앞의 피연산자가 true라면 뒤의 피연산자를 평가하지 않고 바로 true를 산출
- 비트연산자 : &, |
    - 이항연산자로서 피연산자가 정수형, 논리형도 가능
    - & , | : 두 피연산자 모두를 평가해서 산출 결과를 낸다.

```java
8 & 7 --> 00001000 & 00000111 --> 00000000
8 | 7 --> 00001000 & 00000111 --> 00001111
true & true
```
<br>

---
<br>

## while문

```java
while(조건식){
	if(조건식)
		break;
	반복수행문장
}
수행문장 
```

<br>

---
<br>

## 분기제어문

> **break문**
> 
- for문, while문, do-while문을 실행 중지하거나 
조건문인 switch문을 종료할 때 사용
    
    💯 중첩된 반복문에서 바깥쪽 반복문까지 종료시키려면, 
    바깥쪽 반복문에 이름(레이블)을 붙이고 ‘break 이름;’을 사용
    
    ```java
    package day3;
    
    public class BreakOutterExample {
    
    	public static void main(String[] args) {
    
    		Outter : for(char upper='A'; upper<='Z'; upper++) {
    			for(char lower='a'; lower<='z'; lower++) {
    				System.out.println(upper + "-" + lower);
    				if(lower == 'g') {
    					break Outter;
    				}
    			}
    		}
    		System.out.println("프로그램 실행 종료");
    	}
    
    }
    
    ```
    

> **continue문**
> 
- 반복문인 for문, while문, do-while문에서만 사용
- continue뒤에 수행문장은 실행되지 않고,
for문의 증감식 or while문, do-while문이 조건식으로 바로 이동

<aside>
💡 반복문을 종료하지 않고 계속 수행한다는 점이 break문과 다르다.

</aside>

```java
package day3;

public class ContinueExample {

	public static void main(String[] args) {
		for (int i = 1; i <= 10; i++) {
			if(i%2 != 0) {
				continue;
				//홀수는 실행되지 않는다.
			}
			System.out.print(i + " ");
		}
	}

}
```

💯 가변 argument

int exprSum(int… p)

---

## 자바의 api

- System.out : 표준출력장치(screen)
- System.in : 표준입력장치(키보드)
    - .nextInt() : 숫자 입력