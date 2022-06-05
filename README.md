# **linux 명령어**


## **top(table of processes)명령어**


**top명령어는 CPU 사용량, 메모리 사용량 등에 관한 정보를 실시간으로 출력하는 명령어이다.**


**또한 실시간으로 현재 OS의 상태를 출력해줌으로써 OS문제가 있을시 원인을 찾을 수 있는 명령어 중 하나이다.**


**top 명령어를 입력하면 아래와 같은 화면이 출력된다.**
![top명령어 예t시](https://user-images.githubusercontent.com/104613926/172048413-5c466755-6002-49ac-a069-642614cc8e3e.png)


1)첫번째 줄은 시스템 현재시간, 서버 구동시간, 현재 접속 유저수, 
로드 에버리지(1분,5분,15분 동안 시스템 부하량 평균값)을 출력한다.
![가장 윗줄](https://user-images.githubusercontent.com/104613926/172048515-f798a9b4-2820-4b64-b1b5-b1317b9f41a6.png)


2)두번째 줄은 현재프로세스들의 상태(Tasks)를 나타내며 전체프로세스(total)수, 실행중(running)수, 
대기중(sleeping)수, 종료(stoppde)수, 좀비(zombie)수를 출력한다.
![두번쨰 줄](https://user-images.githubusercontent.com/104613926/172048580-04c96bc4-5fbb-420c-9718-99ad33713816.png)


3)세번째 줄은 CPU사용량을 나타내며 사용자 프로세스(us), 커널 프로세스(sy), 프로세스 우선순위(ni), 
사용안하는 비율(id), IO완료를기다리는 비율(wa), 소프트웨어 인터럽트(si), VM에 할당된 비율(st)을 출력한다.
![세번째 줄](https://user-images.githubusercontent.com/104613926/172048660-c042e09d-5c6e-46a9-837e-e5855e892253.png)


4)마지막 줄은 RAM의 메모리 영역과 그 다음 줄은디스크를 메모리 처럼 이용하는 Swap 메모리 영역이다.
총 메모리 양(total), 사용가능 메모리 양(free), 사용중 메모리 양(used), 커널 버퍼 사용메모리 양(buff/cache), 물리적 메모리 양(avail Mem)
![마지막 줄](https://user-images.githubusercontent.com/104613926/172048677-0c782fab-a9a7-4b23-8400-880189c484cf.png)


### **디테일 영역**
**디테일 영역에는 각 프로세스에 대한 상세한 내용이 나옵니다.**
![디테일 영역](https://user-images.githubusercontent.com/104613926/172048991-7c0e1545-9adc-4a7b-be81-cce23db75e6e.png)
+ PID
>PID는 프로세스 ID이며 프로세스를 구분하기 위한 겹치지않는 고유한 값입니다.
+ USER
>해당 프로세스를 실행한 USER 이름 또는 효과를 받는 USER의 이름입니다.
+ PR & NI
>PR : 커널에 의해서 스케줄링되는 우선순위입니다.
>NI : PR에 영향을 주는 nice라는 값입니다.
+ VIRT, RES, SHR, %MEM
>해당 필드들은 프로세스의 메모리와 관련있습니다.
>VIRT : 프로세스가 소비하고 있는 총 메모리입니다. 프로그램이 실행중인 코드, heap, stack과 같은 메모리, IO >buffer 메모리를 포함합니다.
>RES : RAM에서 사용중인 메모리의 크기를 나타냅니다.
>SHR : 다른 프로세스와의 공유메모리(Shared Memory)를 나타냅니다.
>%MEM : RAM에서 RES가 차지하는 비율을 나타냅니다.
+ S : 프로세스의 현재 상태를 나타냅니다.
+ TIME+ : 프로세스가 사용한 토탈 CPU 시간
+ COMMAND : 해당 프로세스를 실행한 커맨드를 나타냅니다.

### **top용 커맨드**
1) k - kill process
>top를 통해 프로세스를 모니터링하며 프로세스를 종료해야겠다고 생각할 수 있습니다. 이때 top에서는 top화면을 보며 프로세스를 종료할 수 있는 기능을 제공해주고 있습니다. 해당 기능을 사용하기 위한 커맨드는 **k**입니다.


2) Sorting the process list
> 디테일 영역에 대해서 원하는 값을 기준으로 정렬하는 방법을 제공합니다. 제공하는 커맨드는 아래와 같습니다. 또한 이미지는 메모리 사용량을 기준으로 정렬한 값입니다.
>> + **‘M’** to sort by memory usage
>> + **‘P’** to sort by CPU usage
>> + **‘N’** to sort by process ID
>> + **‘T’** to sort by the running time
>> + **‘R’** to sort by 오름차순과 내림차순을 토글 변경합니다.


3) Showing a list of threads instead of processes
> top는 기본적으로 프로세스를 기본으로하여 정보를 보여줍니다. 하지만 **H**를 누르면 쓰레드(thread)를 기준으로 보여주는 방식으로 변경됩니다. 변경되는 부분은 요약의 Tasks 영역과 디테일 영역입니다.


4) Filtering through processes
> 프로세스가 너무 많다면 필터링 기능또한 제공해주고 있습니다. 해당 기능을 사용하기 위해서는 **o** 또는 **O**를 누르시면 됩니다. 필터는 COMMAND, %CPU 등등 다양한 방법으로 가능합니다.


******


## **ps(Process Status)명령어**


**ps명령어는 현재 실행중인 프로세스 목록을 보여준다.**


**아파치, 오라클 등 프로그램 프로세스가 정상적인지 확인하거나비정상적인 프로세스가 올라왔는지 확인 하는 등 리눅스 관리 전반적으로 많이 사용되는 명령어이다.주로 파이프라인, grep명령어와 함께 사용하여 특정 프로세스를 확인하는데 많이 사용된다.**


### **ps **

리눅스 버전에 따라 옵션이 차이가 있을 수 있음.이외에도 많은 옵션이 있지만 실제로는 grep명령어와 함께 사용하기 때문에 잘 사용하지 않는다.(ex. ps -ef | grep ~)


|옵션|설명|
|---|---------|
|-e|모든 프로세스를 출력해 준다.|
|-f|풀 포맷으로 보여준다.(UID, PID 등)|
|-l|긴 포맷으로 보여준다.|
|p,-p|특정 PID의 프로세스를 보여준다.|
|-u|특정 사용자의 프로세스를 보여준다.|


**사용예시 및 사용화면**

+ **ps**

![image](https://user-images.githubusercontent.com/104613926/172049814-4094944f-c5b4-46da-b8ef-1f16d43a6006.png)


pid, cmd 등 기본적인 내용만 출력된다. 옵션 없이는 잘 사용하지 않는다.


+ **ps -f(풀 포맷으로 출력)**

![image](https://user-images.githubusercontent.com/104613926/172049911-b7df72cd-8b4b-46f0-91bd-37c12566dfef.png)


uid(user ID), pid(process ID), ppid(parent ID), TTY(프로세스와 연결된 터미널) 등을 표시해준다.

+ **ps -l(긴 포맷으로 출력)**

![image](https://user-images.githubusercontent.com/104613926/172049946-81e2bb5c-0d83-4606-8da7-15cb5acaed23.png)


풀 포맷정보 외에 F(프로세스 플래그), S(프로세스 상태), PRI(우선순위) 등 더 많은 정보를 보여준다.


+ **ps -p 1(프로세스 번호가 1인 프로세스 출력)**

![image](https://user-images.githubusercontent.com/104613926/172049966-b6c6edc8-5487-43e0-9ed9-93a2da86f079.png)


프로세스 번호가 1인 프로세스를 출력해준다. -e옵션과는 같이 사용할 수 없고 ps도 주로 grep과 함께 사용하므로 잘 사용되지 않는 옵션이다.


+ **ps -u apache(계정이 apache인 프로세스들을 )**

![image](https://user-images.githubusercontent.com/104613926/172049986-09822d90-27f2-4abf-904e-4fa2bd4c0f85.png)


apache 계정의 프로세스정보를 출력해주고 있다.


+ **ps -e(모든 프로세스를 출력)**

![image](https://user-images.githubusercontent.com/104613926/172050004-e70b595d-86d5-4bc3-b630-7788f99125f9.png)

숨겨진 프로세스까지 모두 보여준다. 매우 많이 나오기 때문에 more 명령어를 이용하여 보면 좋다.


+ **ps -ef | more(모든 프로세스를 풀 포맷으로 보여준다, more명령어를 줘서 페이지단위로 출력)**

![image](https://user-images.githubusercontent.com/104613926/172050019-38fda4a0-7aaa-4bbd-a173-2fdeb02e708f.png)


프로세스가 매우 많기 때문에 파이프라인을 이용하여 more명렁을 줘서 출력하였다.보통 grep으로 찾을 수 없을때 수동으로 전체 프로세스를 보고자 하는경우 사용한다.


+ **ps -ef | grep apache(모든 프로세스의 출력값을 grep을 이용하여 apache가 포함된 라인들을 출력)**

![image](https://user-images.githubusercontent.com/104613926/172050036-daefb244-8676-4b28-b51c-939f3b8958e3.png)


가장 많이 사용되는 형태이다. 파이프라인을 이용하여 특정 패턴이 있는 프로세스를 찾아 낼 수 있다.주로 oracle 프로세스가 올라와있는지, apache 프로세스가 올라와있는지 등 특정 프로세스가 정상적으로 올라와 있는지 확인하는데 사용된다.


******


## **jobs명령어**


**리눅스 명령어 jobs는 작업이 중지된 상태, 백그라운드로 진행 중인 작업 상태, 변경 되었지만 보고되지 않은 상태 등을 표시하는 명령어다.**



**현재 쉘 세션에서 실행시킨 백그라운드 작업의 목록이 출력디며, 각 작업에는 번호가 붙어 있어 kill 명령어 뒤에 '%번호' 등으로 사용할 수 있다.**



**jobs로 출력되는 백그라운드 작업의 상태값은 다음과 같다.**



|상태|설명|
|----|--------|
|Running|작업이 일시 중단되지 않았고 종료하지 않고 계속 진행 중임|
|Done|작업이 완료되어 0을 반환하고 종료 했음을 의미|
|Done(code)|작업이 정삭적으로 완료되었으며, 0이 아닌 코드를 반환 했음을 의미|
|Stopped|작업이 일시 중단|
|Stopped(SIGTSTP)|SIGTSTP 신호가 작업을 일시 중단|
|Stopped(SIGSTOP)|SIGSTOP 신호가 작업을 일시 중단|
|Stopped(SIGTTIN)|SIGTTIN 신호가 작업을 일시 중단|
|Stopped(SIGTTOU)|SIGTTOU 신호가 작업을 일시 중단|


### **jobs옵션**


|옵션|설명|
|----|--------|
|-l|프로세스 그룹 ID를 state 필드 앞에 출력|
|-n|프로세스 그룹 중에 대표 프로세스 ID를 출력|
|-p|각 프로세스 ID에 대해 한 행씩 출력|
|command|지정한 명령어를 실행|
