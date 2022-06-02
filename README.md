# 오픈소스SW개론 과제2

## 20194519 홍아현


### 리눅스 명령어
---
### 1) top 명령어
 > table of process의 약자로 CPU와 메모리 이용에 관한 정보를 표시하는 작업 관리자 프로그램


 > 얼마나 많은 처리량과 메모리가 사용되는지, 실행 중인 프로세스에 관한 기타 정보 등을 보여줌

!<img src="https://user-images.githubusercontent.com/97158484/171333358-f1a00178-6ca5-492c-bf9a-4195031a2da1.PNG" width="90%" height="90%"/>
* PID: 프로세스 ID, USER: 사용자 ID, PRI: 프로세스 우선순위, NI: NICE 값, VIRT: 가상 메모리 사용량, RES: 현재 페이지가 상주하고 있는 크기, SHR: 메모리 총합
* S: 프로세스 상태, %CPU: 프로세스가 사용하는 CPU 사용률, %MEM: 프로세스가 사용하는 메모리 사용률, TIME+: 프로세스 시작된 후 경과된 시간, COMMAND: 실행된 명령어

- **top 실행 전 옵션**


|옵션|설명|                                      
|:---:|:---:|                                   
|-b|배치모드 출력|                                
|-n|top 실행주기를 설정|

- **top 실행 후 옵션**


|옵션|설명|
|:---:|:---:|
|shift + t|실행된 시간이 큰 순서로 정렬|
|shift + m|메모리 사용량이 큰 순서로 정렬|
|shift + p|cpu 사용량이 큰 순서로 정렬|
|k|프로세스 종료|
|l|첫 번째 행 표시/비표시|
|u|입력한 유저 소유의 process만 표시|
|space bar|Refresh|
|d[sec]|설정된 초 단위로 Refresh|
|q|명령어 종료|

---
### 2) ps 명령어
> process status의 약자로 현재 실행중인 프로세스 목록과 상태를 보여줌

!<img src="https://user-images.githubusercontent.com/97158484/171336058-093c0115-5de2-4b25-a68e-2e4ad8a4ab6c.PNG" width="40%" height="40%"/>
 _→ 기본적인 내용만 출력(PID, TTY, TIME, CMD)_

 - **주요 옵션**


|옵션|설명|
|:---:|:---:|
|-e|모든 프로세스를 출력|
|-f|full format으로 보여줌|
|-l|long format으로 보여줌|
|p, -p|특정 PID 프로세스를 보여줌|
|-u|특정 사용자의 프로세스를 보여줌|
* 실제 grep 명령어와 함께 자주 사용 됨

![캡처3](https://user-images.githubusercontent.com/97158484/171337034-ad78a098-ff31-4546-b638-beb54217fe94.PNG)
 _→ 모든 프로세스의 출력 값을 grep 명령어를 이용하여 hah가 포함된 라인들을 출력하여 보여줌_



!<img src="https://user-images.githubusercontent.com/97158484/171336833-4ad5e0d1-200a-49fa-84e7-009407bdd907.PNG" width="40%" height="40%"/>
 _→ full format 으로 출력(UID, PID, PPID, TTY 등을 표시)_

#### <ps와 top의 차이점>
 - ps는 한 시점에 proc에서 검색한 CPU 사용량이고 top은 proc에서 일정 주기로 합산해서 CPU 사용률을 출력
---
### 3) jobs 명령어
> 작업의 상태를 표시하는 명령어로 현재 쉘 세션에서 실행시킨 백 그라운드 작업의 목록이 출력됨

 - **주요 옵션**


|옵션|설명|
|:---:|:---:|
|-l|프로세스 그룹 ID를 state 필드 앞에 출력|
|-n|프로세스 그룹 중에 대표 프로세스 ID를 출력|
|-p|각 프로세스 ID에 대해 한 행씩 출력|
|command|지정한 명령어 실행|
|%[Number]|해당 번호의 작업 정보 출력|

 - **jobs 명령어로 알 수 있는 세션의 상태 값**


|상태|설명|
|:---:|:---:|
|Running|작업이 계속 진행 중임|
|Done|작업이 완료되어 0을 반환하고 종료|
|Done(code)|작업이 정상적으로 완료되어 0이 아닌 코드를 반환 함|
|Stopped|작업이 일시 중단|
|Stopped(SIGTSTP)|SIGTSTP 신호가 작업을 일시 중단|
|Stopped(SIGSTOP)|SIGSTOP 신호가 작업을 일시 중단|
|Stopped(SIGTTIN)|SIGTTIN 신호가 작업을 일시 중단|
|Stopped(SIGTTOU)|SIGTTOU 신호가 작업을 일시 중단|

 - **기호**


|상태|설명|
|:---:|:---:|
|+|현재 실행되고 있는 또는 실행 예정인 프로세스|
|-|현재 진행중인 job이 끝나면 바로 다음에 수행될 프로세스|

!<img src="https://user-images.githubusercontent.com/97158484/171382545-6de162a3-3cf5-4bcd-b977-db3de07da6d3.PNG" width="50%" height="50%"/>
 _→ 백그라운드에서 명령어 실행하기 위해 & 붙임_
 
---
### 4) kill 명령어
> 프로세스에 특정한 signal을 보내는 명령어로 일반적으로 종료되지 않는 프로세스를 종료시킬 때 많이 사용함


> 시스템에 문제가 생겨 해당 프로세스를 터미널에서 종료시킬 경우 유용하게 쓰임

 - **주요 옵션**


|옵션|설명|
|:---:|:---:|
|[pid]|종료 시킬 프로세스 ID나 프로세스 이름 지정|
|-l|시그널 리스트 출력|
|-s|전달할 시그널의 종류를 지정|
|-1|-HUP 프로세스를 재활성화|
|-15|프로세스 작업 종료|
|-9|프로세스를 강제로 종료|

!<img src="https://user-images.githubusercontent.com/97158484/171344208-23a394a2-5f73-424d-aa77-cf046ae0ebbf.PNG" width="80%" height="80%"/>

_→ 시그널 번호와 시그널 이름은 매치되어서 보여줌_

 - **사용법**


` ps -ef ` 

→ 동작중인 프로세스 확인  

→ 너무 많은 목록이 뜨면 grep 명령어 이용하여 구체적으로 검색

`kill [옵션] PID `

→ 종료 시키고 싶은 프로세스 ID 입력
 
 #### <특정 이름의 프로세스 모두 종료하기>
```
kill `ps -ef | grep 프로세스 이름 | grep -v grep | awk '{print $2}'`
```
---
### vim 에디터
---
- **매크로 사용방법**
> 매크로란 같은 동작을 반복하게 해주는 것
1) `q + a(레지스터)`
- 특정 알파벳(a)에 매크로 저장하여 recording 시작
2) 반복을 위해 원하는 동작 실행
3) `q`
- recoding 종료
4) 기록한 매크로 실행


① `@a(레지스터)`
- 1회 실행


② `@@`
- 방금 실행한 매크로 실행


③ `[Number]@a(레지스터)`
- Number 수 만큼 반복 실행


!<img src="https://user-images.githubusercontent.com/97158484/171387509-db367d03-9676-4a90-b4cd-17b4c54d9516.PNG" width="50%" height="50%"/>
 
 
 _→ 명령모드에서 매크로 시작하면 아래 recoding @a 표시가 뜨면서 매크로 기록이 시작됨_
 
 
 <레지스터에 저장된 매크로 확인>


!<img src="https://user-images.githubusercontent.com/97158484/171389479-0afcf700-1e95-47bc-b8ca-36ec88c6d204.PNG" width="60%" height="60%"/>
 
 
 `:register [레지스터]`
 - 명령어를 입력하여 a 레지스터에 저장된 내용을 확인
 
