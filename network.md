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
elinks <url>   
텍스트 모드 웹 브라우저에서 GUI를 사용할 수 없을 때   
웹서버가 동작중인지 혹은 정보를 얻어오는지 체크   
   
