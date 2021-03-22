# network 란?
- 컴퓨터와 컴퓨터가 어떻게 소통하는 방식

## A컴퓨터에서 B컴퓨터에게 무언가를 보낼때 전달되는 물질
1) Copper (구리) - 전기신호 (+2.5V[1], -2.5V[0])
2) Fiber opfical (광섬유) - 빛(켜지면 [1], 꺼지면 [0])
3) Radio wave (전파,무전) - 전파
    - 전체를 통틀어서 ```전자기파```

## 전자기파
전자기파는 ```300000km/s``` 의 속도를 가지고있음

# 레거시 네트워크
## 1) LAN (Local Area Network)
## 2) WAN (ISP : 인터넷 서비스 제공자 KT,U+,SK)
## 3) MAN
## 4) Internet (전세계에 연결되어있는 인터넷 망)

- 게이트웨이 : 서로다른 네트워크 장비를 연결해주는 장치
- 프로토콜 : 서로 커뮤니케이션하기위한 모든 수단


(참고 : https://ykarma1996.tistory.com/13)

# 통신방식

## 1) Unicast (1:1 통신)
## 2) Broadcast (1:N 불특정다수 통신)
## 3) Multi cast (1:M 특정다수 통신)
- (ex : U+ 인터넷 tv를 신청했을때 특정인물들은 150개의 채널만 지원, 특정다수는 300개의 채널을 볼수있는 권한을 주는 통신 등등...

# 주소 종류
## 1) 물리적 주소 (MAC : media에 따라서 접근방법이 달라짐,48bit, IEEE 에서 MAC 주소를 관리)
  - 변하지 않는 주소
## 2) 논리적 주소 (IP 주소,IANA에서 관리,32bit)
  - 시간과 장소에 따라서 변하는 주소

# OSI 7 계층 (통신을 체계적으로 하기위해 만들어짐)
## 7. Application layer (응용 계층) 
- Chrome, Kakaotalk, Game 등등 - 네트워크를 이용한 응용 프로그램들
## 6. Presention layer (표현 계층)
- 카카오톡에서 이미지,음성,동영상 등의 데이터를 표현하는 방법- ASCII,JPG,MP4,MP3 등등
## 5. Session layer (연결 계층)
- 연결을 시작, 유지, 종료 를 담당
## Upper layer
-----------------
## Dataflower layer
## 4. Transport layer
  - Broad Band (주파수 분할 방식) : 케이블 하나로 여러가지 주파수를 보낸다.
  - Base Band (시분할 방식)
  - 1460byte(Segement)
  - 분할/합치는과정, 에러제어/흐름제어
  - UDP,TCP
  - UDP : 에러제어를 하지않음. (연결이 끊겼을때 무시하겠다는 뜻)
  - TCP : 에러제어를 한다. (연결이 끊겼을때 무시하지않음)
  - Port : 포트의 번호7계층의 서비스와 연결되어있다. 어떤 응용프로그램과 연결되어있는지 알 수 있다.
## 3. Network layer
  - packet(ppu)
  - Routing(경로결정)
## 2. Datalink layer
  - [Desctination MAC][SourceMAC][Type][p acket1500][5cc]

## 1. Physical data layer (물리 계층)
  - bit(pdu) 열 변환 (신호 전달방식을 결정)

## SI
- Developer : 개발자
- SE(System Enginer) : 서버를 다루는 엔지니어
- NE(Network Enginer)

## Network type (Topology)
1. BUS

2. Star

3. Ring
  -fddi

## Ethernet


