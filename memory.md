# Memory   
## 메모리 사용용량 확인   
free   
```
$ free -t
        total   used    free    shared    buff/cache  available
mem:   222222   1111  111111     23443     35353       2111111
swap:
total:

# 시간(초)마다 표시
$ free -s 5
```

vmstat
```
# 3초마다 메모리 표시
$ vmstat 3

# 2초마다 10번 반복
$ vmstat 2 10
```

# CPU   
## cpu 사용량 표시   
```
# 3초마다 표시 시간과 함께
$ iostat -c -t 3 

$ dstat -c -t 3

# top에서도 확인가능
$ top
'Shift + p' 로 CPU usage 정렬

#CPU 정보 확인
$ cat /proc/cpuinfo
```
   
# Run level     
##     
0. halt 시스템종료    
1. Single user mode 시스템 복원모드    
2. Multiuser mode 다중 사용자 모드    
3. Full multiuser mode 텍스트 유저 모드   
4. x 사용하지 않는 모드 유저가 직접 정의하여 사용
5. x11 x윈도우 부팅 GUI환경   
6. reboot 재부팅   
```
# runlevel 확인
$ runlevel
N  5

# runlevel 변경
$ init [number]
```

# kernel   
```
# 커널이름
$ uname -r

# 모든 커널 정보 표시
$ uname -a 

# 커널 버퍼확인
$ dmesg | less
dmesg 명령어는 시스템 부팅 메세지를 확인하는 명령어이다. 또한 커널에서 출력되는 메세지를 일정 수준 기록하는 버퍼 역할을 수행하며, 커널 부팅 중에 에러가 났다면 어느 단계에서 에러가 났는지 범위를 좁히고 찾아내는데 도움이 된다.
```

