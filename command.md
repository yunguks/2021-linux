# 2021-linux

root directory   
![directory](rootdirectory.jpg)

## command   
cd 디렉토리변경    
cd . (현재디렉토리) cd .. (상위 디렉토리)    

```
$ cd   
user@:~$   
    
$ cd ./Music   
user@:~/Music  
``` 
   
ls [옵션] 파일 출력    

```
$ ls -l
-rw-rw-r-- 1 user user 3301828 2월 14 18:00 text.txt

$ ls -a
.  sample.mp3 sample2.mp3 sample2.wav 
.. sample.ogg
```
   
   
rm [옵션]   #파일 제거
```
$ rm file

$ rm -i file
rm: remove file 'file'? (y,n 입력)

$ rm -f file
강제 삭제
```
   
   
mkdir [옵션] #디렉토리 만들기
```
$ mkdir -m 755 test
drwx r-x r-x  type 파일 만듬
```
| d = directory<br>- = 일반file<br>b = block device<br>c = 문자장치(keyboard)<br>l = symbolic link |            파일 접근 권한<br><br>'r w x' / 'r w -' / '- w -'<br>user / group / other           | r = read(읽기)<br><br>w = write(쓰기)<br><br>x = execute(실행) |
|:--------------------------------------------------------------------------------------------------|:----------------------------------------------------------------------------------------------:|:--------------------------------------------------------------:|
| -rwxrw-r--                                                                                       | 일반파일 /user는 읽기,쓰기,실행<br>         /group은 읽기,쓰기 <br>         /other은 읽기 가능 |                                                                |
| drw-r---w-                                                                                       | 디렉토리 /user는 읽기,쓰기<br>         /group은 읽기<br>         /other은 쓰기                 |                                                                |
   
   
man [옵션]   
| 옵션 | 내용 | page | 내용 | page | 내용 |
|:----:|:----:|:----:|:----:|:----:|:----:|
|`man`|명령어의 설명 |1| 일반 명령어 관련 메뉴얼|6 |게임과 화면보호기에 대한 메뉴얼|
| `-a` | 찾고자 하는 명령어의    man 페이지를 모두 출력|2 | 시스템 호출 관련 메뉴얼|7| 리눅스 파일표준,프로토콜, 시그널 목록 정보|
| `-f` | whatis 명령과 동일키워드와 동일한 man 페이지 출력|3| C표준 라이브러리 함수 관련 메뉴얼|8|시스템 관리 명령어 |
| `-k` | apropos 명령과 동일키워드가 포함된 man 페이지 출력|4 | 장치 또는 특수 파일에 대한 메뉴얼 | 9 |커널 관리 정보가 들어있는 메뉴얼|
| `-w` | 찾고자 하는 문자의 man 페이지가 있는 위치 출력|5| 특정 파일들에 대한 정보가 있응 메뉴얼 | |  |
   
   
cp [옵션] [원본파일명] [대상파일명]      
```
#동일한 파일명이 있을 경우 사용자에게 덮어 쓸지 여부 물음
$ cp -i file copyfile

#동일한 파일명 있을 경우 강제로 지우고 복사
$ cp -f file copyfile 

#복사 대상이 이미 존재하고 파일이 더 최신이면 복사 x
$ cp -u file copyfile

#[원본파일명]이 결로일 경우, 그 경로에 있는 하위 디렉토리를 포함해 모두 복사
$ cp -r file copypath
```   
   
   
cat [옵션] [파일이름]   
```
$ cat test.txt
Hello!

# 라인에 번호 붙여 출력
$ cat -n test.txt
1   Hello
```
   
   
## redirect
출력을 파일로 변경 '>' 사용
```
# ls 명령어 test.txt 파일로 저장
$ ls > test.txt
$ cat test.txt
Desktop
Music
Downloads ...

# ls 명령어 test.txt 에 추가하여 저장
$ ls >> test.txt
$ cat test.txt
Hello
Desktop
Music ...
```
   
   
## pipe
'|' 기호를 기준으로 왼쪽 명령어를 오른쪽 으로 전달
```
$ cat test.txt | sort
Desktop
Documents
Downloads ...

$ cat test.txt | grep test
testscript.sh
test.txt
```

