# Network   
## 용어   
ip - 인터넷 통신 관련 규약 / 컴퓨터 네트워크에서 장치들이 서로 인식하고 통신하기 위한 번호(주소)    
DHCP server - 동적 호스트 구성 프로토콜 / IP주소를 컴퓨터 네트워크 인터페이스에 할당하고   
인터넷이나 원격 서버에 접근하기 위한 초기 게이트를 할당하는 서버    
name server - 네트워크나 컴퓨터에 지정된 기호명을 기계가 사용하는 숫자 주소로 변환하는 서버   
DNS server - 도메인 이름에서 IP주소를 추출하는 서버   

simplex - 단방향 전송방식 (TV,라디오)   
half duplex - 반이중 전송박식 (무전기, 양방향가능 하지만 한번에 하나의 전송)   
full duplex - 동시에 양방향 송수신 가능(전화기)   
   
packet - 네트워크를 통해 전송하기 쉽게 자른 데이터 전송 단위    
MAC layer - 매체접근 제어 계층, 여러 대의 컴퓨터 사이에서 네트워크의   
물리적인 접속을 공유하는데 관여, 각 컴퓨터는 고유의 MAC 주소를 가짐   
routing - 어떤 네트워크 안에서 통신 데이터를 보낼 때 최적의 경로를 선택하는 과정   
router - routing 과정에 관여하는 기기    
routing table - 모든 목적지 정보에 대해 해당 목적지에 도달하기 위해서 거쳐야 할 다음 라우터 정보   
   
## interface 확인   
```
# network interface 상태 체크
$ ifconfig
enp0s3: flags=4163<UP,BROADCAST,RUNNING...

# interface의 상태
$ ethtool [network interface name]

# interface 자세한 내용
$ ethtool -S [interface name]

# interface driver 대한 정보
$ ethtool -l [interface name]

# interface의 수정 
$ ethtool -s [interface name] [options]
[options]
speed 10 / 100 / 1000
duplex Full/ Half Duplex
port tp / aui / bnc / mii / fibre
transceriver internal / external
auto-negotiation on / off
link detected

# network interface 의 활성화
$ sudo ifup [network interface]

# netowrk interface 의 비활성화
$ sudo ifdown [network interface]

# 활성, 비활성 network interface 보여줌
$ ifconfig -a

$ cd /etc/network
$ ls 
if-down.d if-post-down.d if-pre-up.d if-up.d
/ if-down.d interface 비활성화시 , if-up.d 활성화시 사용

# 모든 interface 정보제공
$ ip a

# ip command 사용 방법
$ ip help
```
*ip command참조(https://www.howtogeek.com/657911/how-to-use-the-ip-command-on-linux/)

## ping
```
# 도움말
$ ping -h

# 소리 나는
$ ping -a 10.0.2.2

# 패킷 간의 응답속도에 맞춰 패킷보내기
$ ping -A 10.0.2.2

# 브로드캐스트 주소에 ping 가능게한다
$ ping -b www.~~

# 패킷횟수 정하기
$ ping -c [number] 10.0.2.2

# 타임스탬프 출력
$ ping -D 10.0.2.2

# 패킷 간 간격 조절
$ ping -i [number] 10.0.2.2
```
*ping 참조(https://blog.naver.com/o0iwishu0o/221260788272)

## web browsing   
elinks [url]   
텍스트 모드 웹 브라우저에서 GUI를 사용할 수 없을 때   
웹서버가 동작중인지 혹은 정보를 얻어오는지 체크    
!<pic.elink.jpg>  
!<pic.elink2.jpg>
   
## transferring file   
wget [url]   
웹 서버로 부터 원하는 웹사이트 정보를 가져와 저장   
```
# HTML페이지에서 표현 가능한 모든 이미지와 모든 것을 가져옴
$ wget -p <www.wiley.com>

# .html 파일을 브라우저로 열 때 깨지는 현상을 막기 위해서 로컬 파일 이름으로 바꿈
$ wget -pk <www.wiley.com>

# 원본 파일과 로컬 파일 이름으로 바꾼 파일 둘다 만들어줌
$ wget -pkK <www.wiley.com>

# 도움말 표시
$ wget -h

# 백그라운드 작동
$ wget -b <www.wiley.com>
```
   
curl   
wget과 유사하나 SCP,SFTP,LDAP,DICT 등 다양한 프로토콜 지원   
```
# txt 파일로 받기
$ curl -o <www.wiley.com>

# html 파일로 받기
$ culr -O <www.wiley.com>
```
   
lftp   
FTP 서버에서 네트워크를 통해 문서를 가져올때 연결
```
$ lftp ftp.kaist.ac.kr
lftp ftp.kaist.ac.kr:~> pwd
ftp://ftp.kaist.ac.kr
lftp ftp.kaist.ac.kr:~> ls
drwxr-xr-x   17  1000   1000     4096 Feb 16 10:30 Archlinux
...

# 파일 다운 받기 / get (한 파일)
$ lftp ftp.kaist.ac.kr
lftp ftp.kaist.ac.kr:~> cd apache/accumulo/1.10.1
cd 성공, cwd=/apache/accumulo/1.10.1
lftp ftp.kaist.ac.kr:/apache/accumulo/1.10.1> ls
-rw-rw-r-- 1   1000  1000  23880434 Dec 22 19:16 accumulo-1.10.1-bin.tar.gz
-rw-rw-r-- 1   1000  1000  23880434 Dec 22 19:16 accumulo-1.10.1-src.tar.gz
lftp ftp.kaist.ac.kr:/apache/accumulo/1.10.1> get accumulo-1.10.1-src.tar.gz

# 파일 다운 받기 / mirror (한 디렉토리)
$ mkdir test
$ lftp ftp.kaist.ac.kr
lftp ftp.kaist.ac.kr:~> cd apache/accumulo
cd 성공, cwd=/apache/accumulo
lftp ftp.kaist.ac.kr:/apache/accumulo> mirror 1.10.1 /test
```   
   
scp   
나의 로컬에 있는 데이터를 전송할 때   
```
# 단일 파일
$ scp <파일명><원격지 id>@<원격지 ip>:<받는위치>

# 디렉토리
$ scp <디렉토리명><원격지 id>@<원격지 ip>:<보낼 경로>
```
   
rsync    
서버간 또는 서버내 파일전송, 동기화
```
# archive 모드로 타임스탬프,링크,퍼미션,그룹,장치 등의 파일 보존
$ rsync -a [보낼경로] [받을경로]

# 상세 정보 출력
$ rsync -v [보낼경로] [받을경로]

# 하위 디렉토리 까지 복사
$ rsync -r [보낼경로] [받을경로]

# 데이터 압축 전송
$ rsync -z [보낼경로] [받을경로]
```   
   
NFS   
공유된 원격 호스트의 파일을 로컬에서 사용할 수 있도록 개발된 파일 시스템   
```
# 공유된 파일 보기
$ sudo vi /etc/exports 

# 서버로 부터 공유할 수 있는 디렉토리 확인
$ sudo exportfs -rv

# 로컬 시스템으로 부터 공유할 수 있는 디렉토리 확인
$ sudo showmount -e
```
