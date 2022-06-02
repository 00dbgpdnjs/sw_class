# 과제
## 리눅스 명령어
### 1. top 명령어
리눅스 시스템이 실행되고 난 후 부터 지금까지의 시간과 시스테멩 로그인된 사용자 수 그리고 시스템 부하율을 표시하는 명령어인 uptime의 결과를 가장 상단에 표시해주며, 그 아래로 프로세스 수치, CPU 정보, 메모리 정보를 보여주고, 각 프로세스 별 부하율과 상태를 표시해준다.


1. 사용 구문

   `top [옵션]`

2. 사용 예시

- 옵션 없이 명령어를 실행하면 interval 간격(기본 3초)으로 화면을 갱신하며 정보를 보여준다.

   `$ top`

- b 옵션을 사용해 순간의 정보를 확인할 수 있다.

   `$ top -b`

- n 옵션을 사용하여 top 실행 주기를 2번 반복하도록 한다.

   `$ top -n 2`


3. top 실행 후 명령어

- shift + p : CPU 사용률 내림차순
- shift + m : 메모리 사용률 내림차순
  <img width="524" alt="3top_m" src="https://user-images.githubusercontent.com/81615868/171553986-2610ae59-a2b0-4e10-bfd9-3329e3110fe7.png">


- shift + t : 프로세스가 돌아가고 있는 시간 순
- k : kill. k 입력 후 PID 번호 작성. signal은 9
- f : sort field 선택 화면 -> q 누르면 RES순으로 정렬
- a : 메모리 사용량에 따라 정렬
- b : Batch 모드로 작동
- 1 : CPU Core별로 사용량 보여줌
---
### 2. ps 명령어
현재 실행중인 프로세스 목록을 확인할 수 있따.
pocess status의 약자이다.

1. 사용 구문

   `ps [옵션]`

2. 사용 예시


- pid, cmd 등 프로세스의 기본적인 내용만 출력

   `$ ps`
   
  <img width="279" alt="5ps옵션x" src="https://user-images.githubusercontent.com/81615868/171554073-7084622f-80df-4570-b606-8be23447a4d4.png">  

- 모든 프로세스를 출력

   `$ ps -e`
- 풀 포멧으로 출력 (uid, pid, ppid, TTY 등)

   `$ ps -f`

- 긴 포맷으로 출력 (풀 포맷 + F, S, PRI 등)

   `$ ps -l`

- 프로세스 번호가 1인 프로세스를 출력

   `$ ps -p 1`

- 계정이 seek인 프로세스들을 출력

   `$ ps -u seek`

- 모든 프로세스를 풀 모맷으로 출력, more 명령어를 이용하여 페이지 단위로 출력

   `$ ps -ef | more`

- 모든 프로세스를 풀 포멧으로 출력한 목록에서 grep을 이용해 seek이 포함된 행을 출력

   `$ ps -ef | grep seek`
---
### 3. 명령어 jobs

작업이 중지된 상태, 백그라운드로 진행 중인 작업 상태, 변경 되었지만 보고되지 않은 상태 등을 표시하는 명령어다.

1. 사용법

   `jobs [옵션] [job ID]`

   `jobs -x command [args]`


2. 옵션

| 옵션|설명|
|:---: | :---: |
| -l|프로세스 그룹 ID를 state 필드 앞에 출력|
|-n|프로세스 그룹 중에 대표 프로세스 ID를 출력|
|-p|각 프로세스 ID에 대해 한 행씩 출력|
|command| 지정한 명령어를 실행|

3. jobs로 알 수 있는 세션의 상태 값

|상태|설명|
|:---: | :---: |
|Running| 작업이 일시 중단되지 않았고 종료하지 않고 계속 진행 중임|
|Done| 작업이 완료되어 0을 반환하고 종료 했음을 의미|
| Done(code)| 작업이 정삭적으로 완료되었으며, 0이 아닌 코드를 반환 했음을 의미|
|Stopped|작업이 일시 중단|
| Stopped(SIGTSTP)|SIGTSTP 신호가 작업을 일시 중단|
|Stopped(SIGSTOP)|SIGSTOP 신호가 작업을 일시 중단|
|Stopped(SIGTTIN)|SIGTTIN 신호가 작업을 일시 중단|
|Stopped(SIGTTOU)|SIGTTOU 신호가 작업을 일시 중단|
---
### 4. kill 명령어

프로세스에 시그널을 보내 원하는 작업을 하게 한다.

1. 사용 구문

   `kill [옵션] [pid]`
   
   특정 프로세스를 죽이고 싶다면 ps 명령어를 통해 해당 프로세스의 pid를 얻고 kill 명령어의 파라미터로 넘겨 실행하면 프로세스를 종료시킬 수 있다.

2. 사용 예시

- pid가 12345인 프로세스를 종료

  `$ kill 12345`

- pid가 12345인 프로세스를 강제 종료

  `$ kill -9 12345`

  `$ kill -SIGKILL 12345`

- kill 명령어에서 지원하는 시그널 목록을 출력

  `$ kill -l`
## vim 에디터에서 매크로 사용방법

1. 사용 방법

    q눌러서 단축키 지정하면 recording 되서 이때부터 기억 -> q로 매크로 끝냄 -> @ 단축키 + 무슨 매크로 (지정한걸 기억해서 똑같은걸 함)

2. 사용 예시

    `qaOTODO<Esc>q@a`

    a 매크로 recording 시작 -> 입력모드 -> "TODO" 입력 -> 일반모드 -> recording 종료 -> 매크로 중 a 매크로 실행되어 현재 라인을 다음 줄로 밀고 TODO가 입력됨
    
      <img width="217" alt="vim1" src="https://user-images.githubusercontent.com/81615868/171560546-22715d01-aa4e-4640-b1d5-90394e6a5736.png">
      
      <img width="221" alt="vim2" src="https://user-images.githubusercontent.com/81615868/171560674-d5936425-88cc-4ab9-b5bf-c9c6ecdd14c7.png">
