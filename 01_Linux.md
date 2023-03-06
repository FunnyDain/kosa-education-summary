## 01. 특징 & 구조

- 대표적 배포판 : 우분투, centOS(실습)
- 서버용 운영체제
- 구조
    - 커널 : 프로세스,메모리,파일 시스템 관리 / 자원 초기화,제어
    - 셸 : 사용자 인터페이스, 사용자와 커널 사이 중간관리자
    - 응용프로그램
- 실습 환경으로 가상환경을 사용, 그 중 **VMWare 제품군**을 널리 사용  
<br>

---
<br>

## 02. 명령어

> **기본 명령어**
> 
- **pwd**
    
    : 현재 위치한 디렉토의 절대경로를 표시
    
- **ls**
    
    : 현재 위치한 디렉토리 내 파일/디렉토리 목록을 표시
    
    | 옵션 | 설명 |
    | --- | --- |
    | -a | 숨긴파일을 포함한 모든 항목 표시 |
    | -d | 디렉토리 정보만 표시 |
    | -F | 디렉토리는 /, 실행가능 파일은 *, 소켓파일은 =, 링크인 경우 @를 파일이음 뒤에 표시 |
    | -l | 각 항목의 상세 정보들을 함께 표시 |
    | -m | 각 항목들을 쉼표로 구분하여 표시 |
    | -r | 항목들을 역순으로 표시 |
    | -R | 하위 디렉토리의 내용들도 표시 |
    | -s | kb 단위로 표시 |
    | -t | 최종 수정시간을 기준으로 표시 |
    | -u | 최종 액세스 시간 기준으로 표시 |
    
- **cd {경로}**
    
    : change directory, 뒤에 덧붙여진 경로로 이동하는 명령어
    
- **mkdir {디렉토리명}**
    
    : make directory, 디렉토리를 생성
    
- **cp {복사할 대상} {붙여넣을 경로 또는 새 파일명}**
    
    : copy, 파일 또는 폴더 복사
    
    ⚠️ 디렉토리를 복사할 시에는 cp뒤에 -r
    
- **mv {옮길 대상} {대상 디렉토리 또는 새 파일명}**
    
    : move, 파일이나 디렉토리를 옮기거나 이름을 변경
    
- **rm {삭제할 대상}**
    
    : remove, 파일이나 디렉토리를 삭제
    
    ⚠️디렉토리를 삭제할 때는 rm 뒤에 -r, 비어 있다면 rmdir로도
    
- **sudo {명령어}**
    
    : 최고관리자 권한
    
    ```markdown
    sudo apt update
    sudo rm -r importantFolder
    ```
    
- **cat {명령어}**
    
    : concatenate : 연결시키다, 연관시키다, 파일 내용 출력
    
- **기타**
    
    
    | 명령어 | 뜻 |
    | --- | --- |
    | touch | 파일 생성 또는 수정시간 변경 |
    | head, tail | 파일의 첫 10행, 마지막 10행 출력 |
    | file | 파일의 종류를 표시 |
    | clear | 화면 지움 |
    | man | manual, 명령어 help |

> **사용자 & 그룹**
> 
- 기본 root 모든 권한을 가진 슈퍼유저 su
- 사용자 etc/passwd 파일, 그룹은 /et/group 파일 정의

| 명령어 | 뜻 |
| --- | --- |
| useradd | 사용자추가 |
| passwd | 비밀번호 지정 |
| usermod | 사용자 속성 지정 |
| userdel | 사용자 삭제 |
|  |  |
| groups | 사용자가 속한 그룹 출력 |
| groupadd | 새로운 그룹 생성 |
| groupmod | 그룹속성 변경 |
| groupdel | 그룹삭제 |

> **File Permission**
> 
- 권한의 종류
: 읽기(read) + 쓰기(write) + 실행하기(execute)
- **ls -l or ll**

<img src="https://pbs.twimg.com/media/FULaVQoUEAE4Unj?format=jpg&name=900x900">  
  
<br>

> **Link**
> 
- **심볼릭 링크**
    
    ```markdown
    #ln -s 링크대상파일이름 링크파일이름
    ```
    
    - 원본과 다른 아이노드 = 다른 파일 관리
    - 경로 단축
    - 원본 삭제시, 구실 x
- **하드링크**
    
    ```markdown
    #ln 링크대상파일이름 링크파일이름
    ```
    
    - 같은 아이노드 값
    - 데이터 안전 보관
    why? 원본 삭제시, 삭제 해도 그대로
- **I-node**
    
    : 파일이나 디렉토리 생성시 임의번호
    

> **rpm 명령어 (Redhat Packgage Manager) ⇒<br>
yum 명령어 (Yellowdog Update Manager) ⇒<br>
dnf 명령어 (Dandified YUM)**
> 
- 다운로드, 점차 개선되어 dnf
    
    
    | 명령어 | 뜻 |
    | --- | --- |
    | dnf -y install 패키지명 (y는 yes) | 기본설치 |
    | yum localinstall rpm파일명.rpm | RPM 파일 설치 |
    | dnf check-update | 업데이트 가증 목록 |
    | dnf update 패키지명 | 업데이트 |
    | dnf remove 패키지명 | 삭제 |
    | dnf info 패키지명 | 정보 확인 |

> **압축**
> 
- 명령어, 확장명 둘 다 **tar**
    
    
    |  | 종류 |
    | --- | --- |
    | 동작 | c(묶기), x(풀기), t(경로확인) |
    | 옵션 | f(파일), v(과정보이기), J(tar+gzip), j(tar+bzip2) |
    
    ```markdown
    #tar cvf my.tar /etc/sysconfig/ -> 묶기
    #tar cvfJ my.tar.xz /etc/sysconfig//etc/sysconfig/ -> 묶기 + xz압축
    #tar xvf my.tar -> tar 풀기
    #tar xvfJ my.tar.xz /etc/sysconfig/ -> xz압축 해제 + tar풀기
    ```
    

> 파일 위치 검색
> 

<aside>
💡 find [경로][옵션][조건][action]

</aside>

<br>  

---
<br>

## 03. vi Editor

<img src="https://mblogthumb-phinf.pstatic.net/MjAxNzA0MjNfMzAg/MDAxNDkyOTM5NDAyOTYw.5WQUJoo8Ar2SslswAHwvD3UcLk5awbpE0SoifitsZ70g.SW8I-gSEO2793msBScl2AzBPBM_HFVKASU6wvS-7EX8g.PNG.julie_eun1014/동작모드.PNG?type=w800"> 

⚠️ 문서 작성시, 입력모드

> vi 시작
> 

| 명령어 | 뜻 |
| --- | --- |
| vi | 빈 파일을 작성하기 위한 에디터가 열린다. (저장할 때 파일명 지정) |
| vi 파일명 | 해당 파일이 있으면 파일의 내용이 보이고, 없는 파일이면 작성하기 위해 열림 |
| :r(read) filename | 파일 오픈 |

> 입력모드 전환
> 

| 명령어 |  | 뜻 |
| --- | --- | --- |
| i | input | 커서 앞에 입력한다(현재 커서 자리에 입력한다) |
| a | append | 커서 뒤에 입력한다(현재 커서 다음 자리에 입력한다) |
| o | open line | 커서가 위치한 행의 다음행에 입력 |
| I | input | 커서가 위치한 행의 첫 칼럼으로 이동하여 입력 |
| A | append | 커서가 위치한 행의 마지막 칼럼으로 이동하여 입력 |
| O | open line | 커서가 위치한 행의 앞 행에(생성) 입력 |

> 종료
> 

|  | 명령어 | 뜻 |
| --- | --- | --- |
| 마지막 행 모드 | :q | vi에서 작업한 것이 없을 때 그냥 종료한다. |
|  | q! | 작업한 내용을 저장하지 않고 종료한다. |
|  | :w [파일명] | 작업한 내용을 저장, 파일명을 지정하면 새 파일로 저장한다. |
|  | :wq, :wq! | 작업한 내용을 저장하고 vi를 종료한다. |
| 명령모드 | ZZ(shift+zz) | 작업한 내용을 저장하고 vi를 종료한다. |

> 커서 이동
> 

| 명령어 | 뜻 |
| --- | --- |
| k | 위 화살표 |
| j | 아래 화살표 |
| ㅣ | 오른쪽 화살표 |
| h | 왼쪽 화살표 |
| ^ 또는 0 | home키, 현재 행의 첫 컬럼으로 이동 |
| $ | End키, 현재 행의 마지막 컬럼으로 이동 |

> 화면 이동
> 

| 명령어 | 뜻 |
| --- | --- |
| Ctrl + u(up) | 반 화면 위로 이동 |
| Ctrl + d(down) | 반 화면 아래로 이동 |

> 특정 행으로 커서 이동
> 

| 명령어 | 뜻 |
| --- | --- |
| G(Shift + G) | 파일의 마지막 행으로 이동 |
| 10G(Shift + G) | 지정한 행 번호 10로 이동 |
| :10 | 지정한 행 번호 10로 이동(마지막 행 모드) |
| w(word) | 다음 단어로 이동 |

> 내용 수정 & 삭제
> 

| 명령어 | 뜻 |
| --- | --- |
| r | 커서가 위치한 글자를 다른 글자로 수정 |
| cw(change word), #cw | 커서 위치부터 현재 단어의 끝까지 수정,
#에는 수정할 단어의 수를 지정, 예를 들어 3cw는 커서 위치부터 세 단어를 수정 |
| cc | 커서가 위치한 행의 내용을 모두 수정 |
| C | 커서 위치부터 행의 끝까지 수정 |
| r(replace) | 현재 글자 다른 글자로 수정 |
| x, #x | 한 글자 지움
#에는 삭제할 글자수 지정, 예를 들어 3x는 세 글자 삭제 |
| dx(delete word), #dx | 커서 위치의 단어를 삭제
#에는 삭제할 단어 수를 지정 |
| dd, #dd | 커서 위치의 행 삭제,
#에는 삭제할 행의 수를 지정, 예를 들어 5dd는 커서 위치부터 다섯 행을 삭제 |
| D(Shift + d) | 커서 위치부터 행의 끝까지 삭제 |

> 명령 취소, 복사, 잘라내기, 붙여넣기
> 

| 명령어 | 뜻 |
| --- | --- |
| u | 명령 취소 |
| yy, #yy | 커서가 위치한 행을 복사
#에는 복사할 행의 수를 지정한다. 예를 들어 3yy는 세 행을 복사 |
| p | 커서가 위치한 행의 아래쪽에 붙임 |
| P | 커서가 위치한 행의 위쪽에 붙인다. |
| dd, #dd | 커서가 위치한 행을 잘라둔다. 삭제와 같은 기능 |

> 검색 명령어
> 

| 명령어 | 뜻 |
| --- | --- |
| /string | 문자열 검색 |
| n(next) | 다음 위치 검색 |
| N(Next) | 이전으로 위치 검색 |
<br>

---
<br>

## 04. 리눅스 시스템 부팅

> 과정
> 

**[pc 부팅] 전원On ⇒ 바이오스 단계 ⇒**

************************[리눅스 부팅] 부트 로더 단계 ⇒ 커널 초기화 ⇒ systemd서비스 단계 ⇒ 로그인 프롬프트 출력************************(우리 centos로그인 화면************************)************************

---

## 05. systemed 서비스

- 기존의 init 스크립트 대체
- 전체 시스템을 시작하고 관리하는 데 유닉(units)이라 부르는 구성요소 사용
- systemd를 기반으로 서비스를 시작하거나 종료할 때
    
    ```markdown
    **systemctl [옵션][명령][유닛이름]**
    ```
    
    | 명령어 | 뜻 |
    | --- | --- |
    | systemctl | 동작 중 유닛 출력 |
    | systemctl -a | 전체 유닛 출력 |
    | systemctl -t옵션 | 특정 유닛 출력 |
    | systemctl status | 유닛 상태 확인 |
    | systemctl stop | 유닛 정지 |
    | systemctl start | 유닛 시작 |
    

> **systemed와 런레벨**
> 
- 런레벨
    
    “**Run level(작동 수준)"**이란 말 그대로 리눅스 시스템을 어떤 수준으로  작동(부팅)시킬거냐
    
- **(1인유저, CLI, run level 1)** -> **(멀티 유저, CLI, run level 2)**-> **(멀티 유저, CLI, 네트워크, run level 3)**-> **(멀티 유저, GUI, 네트워크, run level 5)**이런 순서로 변함
- 고레벨일수록 자원사용이 많아짐

<img src="https://mblogthumb-phinf.pstatic.net/MjAxNzA0MjNfMzAg/MDAxNDkyOTM5NDAyOTYw.5WQUJoo8Ar2SslswAHwvD3UcLk5awbpE0SoifitsZ70g.SW8I-gSEO2793msBScl2AzBPBM_HFVKASU6wvS-7EX8g.PNG.julie_eun1014/동작모드.PNG?type=w800"/>

<br>

1. **런레벨 1변경(안전모드, 단일 사용자모드)**
    
    ```markdown
    # systemctl isolate rescue.target
    # systemctl isolate runlevel1.target
    # init 1                      
    
    ```
    
2. **기본런레벨 지정(3)**

```markdown
# In -sf /lib/systemd/system/multi-user.target /etc/systemd/system/default.target
```

1. **현재 런레벨 확인**

```markdown
# runlevel
# systemctl -t target
```  
<br>  

---
<br>

## 06. 리눅스 네트워크

> **nmtui**
> 
- 네트워크와 관련된 대부분의 작업의 명령어
- 자동 ip주소 or 고정 ip주소 사용 결정

> **명령어**
> 
- **ifup <장치이름> ifdown <장치이름>**
    
    : 네트워크 장치를 On 또는 Off시키는 명령어
    
- **ifconfig <장치이름>**
    
    : 장치의 IP주소 설정 정보 출력
    
    💯 window는 ipconfig
    
- **nslookup**
    
    : DNS서버의 작동을 테스트
    
- **ping <IP주소 or URL>**
    
    : 해당 컴퓨터가 네크워크상에서 응답하는지를 테스트
    

> 파일
> 
- /ete/sysconfig/network : 네크워크 기본정보 설정파일
- /etc/sysconfig/network-scripts/ifcfg-ens32 : ens32장치 설정 네트워크정보파일
- /etc/resolv.conf : DNS 서버 정보 및 호스트 이름파일
- /etc/hosts : 현 컴퓨터 호스트 name 및 FQDN파일

> **소켓**
> 
- 프로그램이 네트워크에서 데이터를 주고받을 수 있도록 
네트워크 환경에 연결할 수 있게 만들어진 연결부
- 일반적으로 TCP/IP 프로토콜을 기반, 데이터 송수신의 마지막 접점  
<br>
---
<br>

## 07. 프로세스&데몬

> **Process**
> 
- 프로그램의 실행 상태
- 실행 및 종료를 자유롭게 수행
- Foreground Process : 실행시 화면에 나와 사용자와 상호작용, 대부분 응용프로그램
- BackgroundProcess : 실행해도 화면x

> **Daemon**
> 
- 항상 수행되고 있는 프로세스
- 사용자가 직접 제어하지 않고 백그라운드에서 수행
- 주로, 시스템 스타트업 시 자동으로 기동되는 프로세스를 지칭

> 명령어
> 

| ps | 현재 프로세스 상태확인
”ps -ef l grep <프로세스 이름>” |
| --- | --- |
| kill | 프로세스 강제종료
”kill -9 <프로세스 번호>” |
| pstree | 부모, 자식 프로세스 트리형태 |

<br>

---
<br>

## 08. 셀 환경 설정

> **셀 환경 설정 파일**
> 
- 사용자가 로그인할 때마다 자동으로 실행되는 명령어를 저장하는 것
- **시스템 환경 설정 파일**
    - 시스템 사용하는 전체 사용자 공통 환경
    - /etc/profile ****
- **사용자 환경 설정 파일**
    - 각 사용자의 홈 디렉터리에 숨김파일로 생성
        
        ```markdown
        $cat .bash_profile
        $cat .bashrc
        $cat .bach_logout
        ```