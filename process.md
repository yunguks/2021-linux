
## Listing Active Processes   
```
# 현재 실행중인 process 확인
$ ps
PID   TTY     TIME    CMD
6923 pts/0   00:00:00 bash
7110 pts/0   00:00:00 ps

# user의 process 보기
$ ps -u user
~~~

# 모든 process 보기
$ ps -e 
$ ps -el
$ ps -ef
~~~

# 정보 표시
$ ps ax
$ ps aux
$ ps auwx 
$ ps -eo ppid,user,size  / 원하는 정보만 표시

# 계층 구조로 보기
$ ps -ejH
$ pstree

# top
$ top -d 5  / 5초간격으로 표시
$ top -u user / user 의 process 표시
$ top -n 2 10 / 2초간격 10번 표시
$ top -b    / bach 모드

# process 선택하여 보기
$ pgrep name / name을 포함한 process PID
$ pgrep -l name / name을 포함한 process PID,name
$ pgrep -lu user / user 의 process
$ ps -fp $(pgrep name) / name을 포함한 process 찾고 출력

```
   
## Processor priority   
nice / 프로세스의 우선순위를 정하는 명령어   
-20 ~ 19 까지 있으며 작을수록 우선순위   

*PNI도 우선순위이나 조절할 수 없음   
```
# 우선순위에 +N 한 프로세스 실행
$ nice -[N] process
$ nice process / default 값 10인 process 실행

# 이미실행된 NI값에 N을 더한 값 변경
$ sudo renice [N] PID
$ sudo renice [N] -u user / user 의 NI값 변경
```
   
## bg, fg &  
& - 명령어 뒤에 &붙이면 백그라운드로 실행
```
$ sudo apt update &
[1] 6145
```
   
jobs - 백그라운드 프로세스나 중지된 프로세스의 목록 출력    
+는 현재 진행중인 프로세스 -는 바로다음 진행할 프로세스
```
$ jobs
[1]+ Stopped  sudo apt update
[2]  done     cat /var/log/pkglog.bin > logtest.txt
```
   
bg ,fg 프로세스 변경   
*ctrl + z 로 백그라운드로 보내면서 프로세스 멈출수 있음 
```
# 실행중인 프로세스 백그라운드로 변경
$ bg [작업번호]

# 실행중인 프로세스 포그라운드로 변경
$ fg [작업번호]
```
참고(https://jhnyang.tistory.com/395)   
   
## process 종료    
kill   
```
# PID 프로세스 종료
$ kill PID 

# 1번 프로세스 종료
$ kill %1

# 여러가지 옵션
$ kill -[option] PID
```
    
killall - 여러 프로세스 한번에 종료
```
$ killall [option] process
```
   
## shell을 꺼도 실행되는 process   
nohup
```
$ nohup [명령어] &
```
   
## process 예약   
at - 1회성 예약
```
$ at now +5 min 
at> echo hello > test.txt
at> <Ctrl+D> <EOT> /종료

# 예약 목록 list
$ at -l

# 예약 제거
$ at -d [예약번호]

```   
    
crontab file  - 반복 예약
```
# 예약 추가
$ crontab -e
________________________________________________
|# m  h   dom mon dow    command               |
| 00 12    *   *   *     echo hello > test.txt |
|______________________________________________|

# 예약 리스트 확인
$ crontab -l

# 예약 제거
$ crontab -r
```

