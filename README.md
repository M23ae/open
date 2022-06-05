# **linux 명령어**


## **top(table of processes)**


**top명령어는 CPU 사용량, 메모리 사용량 등에 관한 정보를 실시간으로 출력하는 명령어이다.**


**또한 실시간으로 현재 OS의 상태를 출력해줌으로써 OS문제가 있을시 원인을 찾을 수 있는 명령어 중 하나이다.**


**top 명령어를 입력하면 아래와 같은 화면이 출력된다.**
![top명령어 예t시](https://user-images.githubusercontent.com/104613926/172048413-5c466755-6002-49ac-a069-642614cc8e3e.png)


**1)첫번째 줄은 시스템 현재시간, 서버 구동시간, 현재 접속 유저수, 
로드 에버리지(1분,5분,15분 동안 시스템 부하량 평균값)을 출력한다.**
![가장 윗줄](https://user-images.githubusercontent.com/104613926/172048515-f798a9b4-2820-4b64-b1b5-b1317b9f41a6.png)


**2)두번째 줄은 현재프로세스들의 상태(Tasks)를 나타내며 전체프로세스(total)수, 실행중(running)수, 
대기중(sleeping)수, 종료(stoppde)수, 좀비(zombie)수를 출력한다.**
![두번쨰 줄](https://user-images.githubusercontent.com/104613926/172048580-04c96bc4-5fbb-420c-9718-99ad33713816.png)


**3)세번째 줄은 CPU사용량을 나타내며 사용자 프로세스(us), 커널 프로세스(sy), 프로세스 우선순위(ni), 
사용안하는 비율(id), IO완료를기다리는 비율(wa), 소프트웨어 인터럽트(si), VM에 할당된 비율(st)을 출력한다.**
![세번째 줄](https://user-images.githubusercontent.com/104613926/172048660-c042e09d-5c6e-46a9-837e-e5855e892253.png)


**4)마지막 줄은 RAM의 메모리 영역과 그 다음 줄은디스크를 메모리 처럼 이용하는 Swap 메모리 영역이다.
총 메모리 양(total), 사용가능 메모리 양(free), 사용중 메모리 양(used), 커널 버퍼 사용메모리 양(buff/cache), 물리적 메모리 양(avail Mem)**
![마지막 줄](https://user-images.githubusercontent.com/104613926/172048677-0c782fab-a9a7-4b23-8400-880189c484cf.png)


### **디테일 영역**
![디테일 영역](https://user-images.githubusercontent.com/104613926/172048991-7c0e1545-9adc-4a7b-be81-cce23db75e6e.png)

