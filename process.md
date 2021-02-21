
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
