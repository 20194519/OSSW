# 오픈소스SW개론 과제2

## 20194519 홍아현


### 리눅스 명령어
---
#### 1) top 명령어
 * table of process의 약자로 CPU와 메모리 이용에 관한 정보를 표시하는 작업 관리자 프로그램
 * 얼마나 많은 처리량과 메모리가 사용되는지, 실행 중인 프로세스에 관한 기타 정보 등을 보여줌

!<img src="https://user-images.githubusercontent.com/97158484/171333358-f1a00178-6ca5-492c-bf9a-4195031a2da1.PNG" width="90%" height="90%"/>
###### PID: 프로세스 ID, USER: 사용자 ID, PRI: 프로세스 우선순위, NI: NICE 값, VIRT: 가상 메모리 사용량, RES: 현재 페이지가 상주하고 있는 크기, SHR: 메모리 총합
###### S: 프로세스 상태, %CPU: 프로세스가 사용하는 CPU 사용률, %MEM: 프로세스가 사용하는 메모리 사용률, TIME+: 프로세스 시작된 후 경과된 시간, COMMAND: 실행된 명령어

 #### - top 실행 전 옵션
|옵션|설명|                                      
|:---:|:---:|                                   
|-b|배치모드 출력|                                
|-n|top 실행주기를 설정|
#### - top 실행 후 옵션
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
#### 2) ps 명령어
* process status의 약자로 현재 실행중인 프로세스 목록과 상태를 보여줌

!<img src="https://user-images.githubusercontent.com/97158484/171336058-093c0115-5de2-4b25-a68e-2e4ad8a4ab6c.PNG" width="40%" height="40%"/>
 → 기본적인 내용만 출력(PID, TTY, TIME, CMD)

##### - 주요 옵션
|옵션|설명|
|:---:|:---:|
|-e|모든 프로세스를 출력|
|-f|full format으로 보여줌|
|-l|long format으로 보여줌|
|p, -p|특정 PID 프로세스를 보여줌|
|-u|특정 사용자의 프로세스를 보여줌|
* 실제 grep 명령어와 함께 자주 사용 됨

![캡처3](https://user-images.githubusercontent.com/97158484/171337034-ad78a098-ff31-4546-b638-beb54217fe94.PNG)
 → 모든 프로세스의 출력 값을 grep 명령어를 이용하여 hah가 포함된 라인들을 출력하여 보여줌



!<img src="https://user-images.githubusercontent.com/97158484/171336833-4ad5e0d1-200a-49fa-84e7-009407bdd907.PNG" width="40%" height="40%"/>
 → full format 으로 출력(UID, PID, PPID, TTY 등을 표시)

#### <ps와 top의 차이점>
##### - ps는 한 시점에 proc에서 검색한 CPU 사용량이고 top은 proc에서 일정 주기로 합산해서 CPU 사용률을 출력한다
---
### 3) jobs 명령어
