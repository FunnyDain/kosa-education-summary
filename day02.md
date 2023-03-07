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