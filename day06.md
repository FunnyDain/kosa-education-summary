# 객체지향
<br>

### 클래스

> **클래스의 두 가지 용도**
> 
- 라이브러리 클래스 : 실행할 수 없으며 다른 클래스에서 이용하는 클래스
- 실행 클래스 : main 메소드를 가지고 있는 실행 가능한 클래스

## **클래스의 구성 멤버**

**생성자, 필드, 메서드**

```java
public class ClassName{
	//필드 선언
	int fieldName;

	//생성자 선언
	ClassName() {...}

	//메서드 선언
	int methodName(){...}
}
```

### **필드** : 객체의 데이터가 저장되는 곳

```java
//외부 객체--
void method(){
	//Car 객체 생성
	Car myCar = new Car();
	
	//외부에서 필드 사용
	myCar.speed = 60;
}

--------------------------------

//객체 내부--
//필드
int speed;

//생성자에서 사용
Car(){
	speed = 10;
}

//메서드에서 사용
void method(...){
	speed = 60;
}
```

⚠️ 로컬 변수와 다름

| 구분 | 필드 | (로컬)변수 |
| --- | --- | --- |
| 선언위치 | 클래스 선언 블록 | 생성자, 메서드 선언 블록 |
| 존재위치 | 객체 내부에 존재 | 생성자, 메서드 호출 시에만 존재 |
| 사용위치 | 객체 내*외부 어디든 사용 | 생성자, 메서드 블록 내부에서만 사용 |
- 기본타입, 참조타입(배열, 클래스, 인터페이스) 둘 다 가능
- 초기값으로 제공하지 않을 경우,
필드는 객체 생성 시 자동으로 기본값으로 초기화(참조타입은 null)
- 생성자 : new 연산자로 객체 생성시 초기화 역할, 리턴타입 x, 클래스 이름과 동일
- 메서드 : 객체의 동작으로 호출시 실행하는 블록

<br>

---
<br>

### **생성자** : new 연산자를 사용하여 객체를 초기화 = 생성자 사용(호출)

```java
클래스 변수 = new 클래스()
```

💫 객체의 초기화 

필드 초기화 or 메서드를 호출해서 객체를 사용할 준비

- 리턴타입 반드시 생략, 메서드 오버로딩 가능
- this, this(), super, super()를 이용하여 구현하는 것 가능

> 기본 생성자
> 

```java
[public] 클래스(){}
```

- 모든 클래스는 생성자가 존재
- 만약 클래스에 생성자 선언이 없으면 컴파일러는 기본생성자를 바이트코드 파일에 자동으로 추가

> 생성자 선언
> 

```java
클래스(매개변수,...){
	//객체의 초기화 코드
}

public class Car{
	//생성자 선언
	Car(String model, String color, int maxSpeed){...};
}

//생성자 호출_main에서
Car myCar = new Car("그랜저","검정",300);

```

> 필드 초기화
> 

```java
public class Korea{
	//필드 선언
	String nation = "대한민국";
	String name;
	String ssn;

	//생성자 선언
	//this는 현객체
	Korea(String name, String ssn){
		this.name = name;
		this.ssn = ssn;
	}
}

//생성자 호출
Korean k1 = new Korean("박자바","011225-1234567");
Korean k2 = new Korean("김자바","930525-0654321");

//객체 데이터 읽기
k1.name;   //박자바
k2.ssn;    //930525-0654321
```

> **생성자 오버로딩**
> 

: 매개변수의 타입, 개수, 순서를 달리하는 생성자를 여러개 선언

```java
public class Car{
	Car(){...}
	Car(String model){...}
	Car(String model, String color){...}
}
```

> 생성자를 이용한 인스턴스 복사
> 

```java
Car(Car c){
	this(c.color, c.gearType, c.door)
}
```
<br>

---
<br>

## 인스턴스 멤버

- 필드와 메서드는 선언 방법에 따라 인스턴스 멤버와 정적 멤버로 분류될 수 있다.

| 구분 | 설명 |
| --- | --- |
| 인스턴스(instance)멤버 | 객체에 소속된 멤버 (객체를 생성해야만 사용할 수 있는 멤버)
인스턴스 생성시 생성 |
| 정적(static)멤버 | 클래스에 고정된 멤버 (객체 없이도 사용할 수 있는 멤버)
앞에 static키워드
클래스가 메모리가 올라갈때 생성
객체 생성 없이 “클래스 이름.클래스변수명”으로 접근
모든 인스턴스가 하나의 저장공간을 공유하므로 항상 공통된 값을 가짐 |

```java
int iv;   //인스턴스 변수
static int cv;  //클래스 변수(static변수, 공유변수)

void method(){
	int lv = 0;   //지역변수
}
```

⚠️ 클래스 변수 접근시, 객체명.클래스 변수이름 x
      클래스명. 클래스 변수이름로 접근해야함 (객체로 접근하면 헷갈릴 수 있다.)
      클래스 변수 변경시 모든 객체의 클래스 변수가 같이 바뀐다.

<br>

---
<br>

## this

### 1) 다른 생성자 호출, 생성자 this()

공통 코드를 한 생성자에만 집중적으로 작성하고, 
나머지는 this(…)를 사용하여 공통 코드를 가지는 생성자 호출

```java
Car(String model){
	//호출
	this(model, "은색", 250);   
}

Car(String model, String color){
	//호출
	//this메서드 : 생성자 안에서 다른 생성자를 호출하는 용도
	this(model, color , 250);
	//추가적인 실행문
}

Car(String model, String color, int maxSpeed){
	//공통 초기화 코드
	this.model = model;
	this.color = color;
	this.maxSpeed = maxSpeed;
}
```

### 2) 참조 변수 this

```java
public class Car{
	//필드 선언
	String model;
	int speed;

	//생성자 선언
	Car(String model){
		this.model = model;   //매개변수를 필드에 대입(this 생략 불가)
	}

	//메서드 선언
	void setSpeed(int speed){
		this.speed = speed;   //매개변수를 필드에 대입(this 생략 불가)
	}

	//this생략 가능
	void run(){
		this.setSpeed(100);
		System.out.println(this.model + "가 달립니다.(시속 : " + this.speed + "km/h)");
	}

}
```

- 객체 내부에서 인스턴스 멤버에 접근 하기 위해 this사용
- 생성자와 메서드의 매개변수명이 인스턴스 멤버인 필드명과 동일한 경우,
**인스턴스 필드임을 강조하고자 할때 this.인스턴스변수**
- 인스턴스 주소가 저장됨

<br>

---
<br>

## JVM의 메모리 구조

<img src="https://velog.velcdn.com/images/mingseok/post/7805689d-a863-4f8d-a7b1-8339a6fa6fae/image.png"/>

> 메서드 영역 (Method Area)
> 

: 클래스 정보와 클래스 변수가 저장됨

> 호출스택 (Call Stack)
> 

: 메서드의 작업 공간, 메서드가 호출되면 메서드 수행에 필요한 메모리 공간을 할당받고, 메서드가 종료되면 사용하던 메모리 반환
지역변수들이 이 곳에서 만들어짐

💯 스택 자료 구조 특징

제일 마지막에 넣은 데이터를 제일 먼저 꺼냄

> 힙 (Heap)
> 

: 인스턴스가 생성되는 공간, new연산자에 의해서 생성되는 배열과 객체는 모두 여기에 생성
인스턴스변수들이 이 곳에서 만들어짐

<br>

---
<br>

## 출력메서드

- System.out.printf()
- Scanner

```java
next() : String - 한 단어
nextInt() : int - 정수형 숫자
nextDouble() : double - 실수형 숫자
nextLine : String - 한 행, 공백이나 tap도 인정, 개행문자는 읽고 버림
```
<br>

---
<br>

## 클래스다이어그램 멤버들의 접근성 정의

- +: public
- #: protected
- 생략 : default
- -: private