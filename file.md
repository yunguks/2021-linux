
# file
    
## fdisk   
```
# 현재 디스크 및 파티션 보기
$ sudo fdisk -l

$ sudo fdisk /dev/sdb 

Welcome to fdisk (util-linux 2.34).
Changes will remain in memory only, untile you decide to write them.
Be care ful before using the write command.

Command (m for help) :

m 메뉴보기
p 파티션 설정 보기
a 부팅 파티션 설정
d 파티션 삭제
w 파티션 설정 저장
n 파티션 추가
t 파티션 종류 변경
```
    
## parted   
<u>fdisk랑 다르게 변경사항 즉시 기록 주의!</u>

```
$ sudo parted /dev/sdb
Welcome to GNU parted! Type 'help' to view a list of commands
(parted) 입력
```
print   
![parted](print.jpg)
    
mkpart    
![mkparted](mkpart.jpg)
