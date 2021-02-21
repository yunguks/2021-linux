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

