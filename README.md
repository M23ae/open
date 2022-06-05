# **linux 명령어**


## **top(table of processes)**


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
