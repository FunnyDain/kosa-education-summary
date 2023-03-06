# Network&Web Summary
<br>

## 01. OSI 7 Layers vs TCP/IP

> 네트워크
> 
- 컴퓨터와 컴퓨터를 연결해주는 망

> **OSI7 7계층**
> 
- 네트워킹을 위한 물리적 장비부터
실제 서비스를 제공하기 위한 어플리케이션에 이르는 단계의 계층화

> **TCP/IP**  
> 
- OSI 7계층을 ⇒ 4계층으로 정의
- IP(Internet Protocal) : 인터넷 프로토콜
    - 패킷 데이터를 최대한 빨리 목적지로 보내는 프로토콜
    - 작은 단위 ⇒ 순서섞임, 유실 가능성
- TCP(Transmission Control Protocol) : 전송 조절 프로토콜
    - 패킷을 정상적으로 받을 수 있도록 하는 프로토콜(꼼꼼)
    - 대신 느림
    

<aside>
💡 **이 두 가지 프로토콜을 조합하여 인터넷 통신하는 것이 TCP/IP**

</aside>

- 이 프로토콜에 기반하고 있는 것이 인터넷

> **IP Address**
> 
- TCP/IP로 연결된 네트워크에서 각각의 컴퓨터를 구분하기 위해 사용하는 주소
- ‘123.123.123.123’과 같이 4개로 구분되며, 10진수를 사용
- IPv6와 IPv4 비교
    - Pv6(Internet Protocol version 6)란 차세대 인터넷 주소 체계
    
    <img src="https://files.itworld.co.kr/archive/image/2016/10/스크린샷 2017-08-01 오후 5_39_26.jpg"/>
    

- ip 주소검색  
<br>  
---
<br>

## 02. Network Commands

> **ip 주소검색**
> 

| 명령어 | 뜻 |
| --- | --- |
| whoami | 강의실에서 외부로 public하게 나가게 |
| ipconfig | window local ip(cmd에서) |
| ifconfig | Linux centos ip(VMware에서) |

> **Ping (Packet Internet Groper)**
> 
- 네트워크 상태 점검, 진단 명령어
- 작동원리
    1. 네트워크 상태를 확인하려는 대상(target) 컴퓨터를 향해
    IMCP(Internet Control Message Protocol) echo request
    = 패킷(packet, 네트워크 최소 전송단위) 보냄
    2. ICMP echo reply
    = 대상 컴퓨터가 이에 응답하는 메세지를 보냄
    3. 수신,분석

> **Netstat**
> 
- 케이블 / 인터페이스 양호상태
- **nmtui** : ip주소 변경도 가능 _ vm
    
    ⚠️ 변경시 tap키로 이동
    
    ⚠️ 변경하더라도 IP address(window)의 특정 숫자를 맞춰야함
    
    <img src='https://s3.us-west-2.amazonaws.com/secure.notion-static.com/32041795-b444-4aab-afcc-2d71ff2167c5/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230301%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230301T103647Z&X-Amz-Expires=86400&X-Amz-Signature=2bf74073c884b29feeb9bcaeeec0bcd7bb3dd712b4f17d09f0334cd2d1284bb5&X-Amz-SignedHeaders=host&response-content-disposition=filename%3D"Untitled.png"&x-id=GetObject'/>
    
    ⚠️ 변경 후 재부팅 해줘야 적용됌 : init 6
    
    <aside>
    💡 ping을 날려 확인이 가능함
    cmd에서 **ping 바뀐 ip(centos주소)**
    
    </aside>
    
    <img src='https://s3.us-west-2.amazonaws.com/secure.notion-static.com/d655ca53-8aa1-4d0a-8cb6-754c4d229186/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20230301%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20230301T104207Z&X-Amz-Expires=86400&X-Amz-Signature=343a28894685ae70e43b91a36ecf23e82b343173f836795a6eef55bbeb9c599a&X-Amz-SignedHeaders=host&response-content-disposition=filename%3D"Untitled.png"&x-id=GetObject'/>
    
<br>  

---
<br>  

## 03. PuTTY

> **가상 단말기 프로그램**
> 
- 서버는 물리적으로 떨어져 있어도 단말 장비를 통해서 원격으로 접속하여 작업할 필요o
- 이때 윈도우같은 개인 pc 운영체제에서도 서버로 접속할 수 있도록 물리적인 단말장비x, 논리적인 가상 단말기를 제공
- 설치
    
    <img src='https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F686055f9-c6f0-44e9-8482-98cd323eef16%2FUntitled.png?id=a88a0d1f-0a6b-436a-82d9-2ba2cb0cacd6&table=block&spaceId=03fc8029-b352-4927-b6e4-48a615879278&width=1530&userId=905873fb-870c-4d9c-ac87-17e37c1fbe2d&cache=v2'/>
    
- 실행
    
    <img src='https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fd3f37788-929a-4a02-9c43-9ed6b1b0e3f1%2FUntitled.png?id=d3e7a4b0-dffb-4836-be05-8481d168f202&table=block&spaceId=03fc8029-b352-4927-b6e4-48a615879278&width=1530&userId=905873fb-870c-4d9c-ac87-17e37c1fbe2d&cache=v2'/>
    
    ⚠️ 그런데 나는 안되서 ip주소 변경해줌 192.168.37.55  
    
<br>  

---
<br>

## 04. 인터넷

> **프로토콜(Protocol)**
> 
- 네트워크에 연결된 컴퓨터들 간의 통신 규약
- 인터넷 서비스는 모두 TCP/IP를 사용, TCP/IP 계층 중 **응용 계층에 해당**

> **포트(Port)**
> 
- 하나의 컴퓨터에서 여러 개의 네트워크 서비스를 제공하는 경우  
이들을 구분하기 위한 목적

 

> **DNS(Domain Name System) : 도메인 네임 시스템**
> 
- 사람이 읽을 수 있는 도메인 이름(예: [www.amazon.com](http://www.amazon.com/))을 머신이 읽을 수 있는 IP 주소(예: 192.0.2.44)로 변환
    
    <img src="https://media.geeksforgeeks.org/wp-content/uploads/20200822065029/UntitledDiagram.png"/>
    

> **HTTP 프로토콜**
> 
- HTTP(Hypertext Transfer Protocol)
: 웹 브라우저와 웹 서버가 통신하는 프로토콜
- 정적인 웹 페이지 처리방식, 동적인 웹 페이지 처리방식

> **HTTP Request**
> 
- 요청 라인(Request Line) : 메서드 방식, 요청 url
- 요청 헤더(Request Header) : 인코딩 방식
- 요청 본체(Request Body)

<img src="https://www.guru99.com/images/2/032020_0831_GETvsPOSTKe1.png"/>

> ******HTTP Response******
> 
- 상태 라인(Status Line) : 상태 코드와 프로토콜 버전
    - 1xx (Informational) : 조건부 응답
    - 2xx (Successful) : 성공
    - 3xx (Redirection) : 리다이렉션 완료
    - 4xx (Client Error) : 요청 오류
    - 5xx (Server Error) : 서버 오류
- 응답 헤더(Response Header) : 인코딩 방식, 서버 정보
- 응답 본체(Response Body) : 일반적으로 html

<img src='https://www.oreilly.com/api/v2/epubs/9781788622882/files/assets/da10d816-bf87-4a1f-af13-2daccd4b331d.png'/>

> **CSR vs SSR**
> 
- **CSR(Client Side Rendering)**
    
    : **렌더링이 클라이언트 쪽에서 일어남**
    
    - 서버는 요청을 받으면 클라이언트에 HTML과 JS를 보내준다.
    - 클라이언트는 그것을 받아 렌더링을 시작
    
    <img src='https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FEk28V%2FbtrFde42IHr%2Fyb4wyWVcsqkV96kkrpS4Z0%2Fimg.png'>
    

- **SSR(Server Side Rendering)**
    
    **: 서버쪽에서 렌더링 준비를 끝마친 상태로 클라이언트에 전달**
    
    <img src='https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FctbYqm%2FbtrE8OfqPyZ%2FV89cr1aPQZemy8tNmnhLek%2Fimg.png'/>
    

> **SPA & MPA**
> 
- **SPA(Single Page Application)**
    
    **: 한 개(Single)의 Page로 구성된 Application**
    
    - 웹 어플리케이션에 필요한 모든 정적 리소스를 최초 한번에 다운로드
    - 그 이후 새로운 페이지 요청시, 페이지 갱신에 필요한 데이터만 받아서(Ajax) 페이지 갱신
    
    <img src='https://hanamon.kr/wp-content/uploads/2021/03/SPA.png'>
    
- **MPA(Multiple Page Application)**
    
    : 여러 개(Single)의 Page로 구성된 Application
    
    - 새로운 페이지를 요청할 때마다 정적 리소스가 다운로드
    ⇒ 매번 전체페이지가 다시 렌더링
    
    <img src='https://hanamon.kr/wp-content/uploads/2021/03/MPA.png'>
    
<br>

---
<br>

## 05. IED install & setting

> JDK설치
> 
- 11.0.2버전
- 환경변수 설정
- cmd에서 확인 : **java -version**

> 이클립스 설치
> 
- 2021-12(4.22) 버전, jee로 설치

> Tomcat9 설치
> 
- zip으로 설치

⚠️ 설치 후, 이클립스의 Servers에서 tomcat설정해주기

> myweb dynamic프로젝트 생성
> 
- webapp - New - hello.html생성
    - Ctrl + F11 : 톰캣 설정하고 실행
    - localhost:8080/myweb/hello.html
    - ip주소/myweb/hello.html
- webapp - New - myjsp.jsp생성
    
    ```bash
    <%@page import="java.util.Date"%>
    <%@ page language="java" contentType="text/html; charset=EUC-KR"
        pageEncoding="EUC-KR"%>
    <!DOCTYPE html>
    <html>
    <head>
    <meta charset="EUC-KR">
    <title>Insert title here</title>
    </head>
    <body>
    	<%= new Date() %>		<!-- 생성자를 호출한 것이다. 그래서 객체가 생성된다. -->
    	
    </body>
    </html>
    ```
    
    💯 jsp는 .java파일로 변환됨
    

> 인코딩 설정 _ UTF-8
> 
- preference - General - Workspace의 Other변경
  
<br>

---
<br>

## 06. Spring설치

- 이클립스 market - st3로 설치
- legacy project생성 - myspring mvc로
- pom.xml 세군데, properties의 Project Facets에서 java 11버전 변경해주기
- springframework 5.3.25로 변경