# REST
- REST (Representational State Transfer) 은 월드 와이드 웹(www)과 같은 분산 하이퍼미디어 시스템을 위한 소프트웨어 아키텍처의 한 형식이다.

- REST란, "웹에 존재하는 모든 자원(이미지,동영상,DB 자원)에 고유한 URI를 부여해 활용"하는 것으로, 자원을 정의하고 자원에 대한 주소를 지정하는 방법론을 의미
  
- 이런 REST의 형식을 따른 시스템을 [RESTful] 이라고한다.

## CRUD operation, HTTP Method
1. Create : POST (자원 생성)
2. Read : GET (자원의 정보 조회)
3. Update : PUT (자원의 정보 업데이트)
4. Delete : DELETE (자원 삭제)

## REST 구성요소
1. 자원(Resource), URI   
  모든 자원은 고유한 ID를 가지고, ID는 서버에 존재하고 클라이언트는 각자원의 상태를 조작하기 위해 요청을 보낸다. HTTP에서 이러한 자원을 구별하는 ID는 'Students/1'같은 HTTP URI 이다.
2. 행위 (Verb), Method   
  클라이언트는 URI를 이용해 자원을 지정하고 자원을 조작하기 위해 Method를 사용한다. HTTP 프로토콜에서는 GET,POST,PUT,DELETE 같은 Method를 제공한다.
3. 표현 (Representation)   
  클라이언트가 서버로 요청을 보냈을 때 서버가 응답으로 보내주는 자원의 상태를 Representation이라고 한다. REST에서 하나의 자원은 JSON, XML, TEXT, RSS 등 여러 형태의 Representation으로 나타낼 수 있다.

## REST 의 특징
1. 클라이언트 / 서버 구조 (Client-Server)   
  자원이 있는 Server, 자원을 요청하는 Client의 구조를 가진다.
2. 무상태 (Stateless)   
  HTTP는 Stateless 프로토콜 이므로 REST역시 무상태성을 가진다. 클라이언트의 Context를 서버에 저장하지 않는다.
3. 캐시 처리 가능 (Casheable)   
  웹 표준 HTTP 프로토콜을 그대로 사용하므로, 웹에서 사용하는 기존의 인프라를 그대로 활용 가능하다.
4. 계층화   
  API 서버는 순수 비즈니스 로직을 수행하고 그 앞단에 사용자 인증, 암호화, 로드밸런싱 등을 하는 계층을 추가하여 구조상의 유연성을 줄 수 있다.

  ## REST API란?
  - API 란?   
    데이터와 기능의 집합을 제공하여 컴퓨터 프로그램간의 상호작용을 촉진하고 서로 정보를 교환 가능하도록 하는 것
  - REST API의 정의   
    REST기반으로 서비스 API를 구현한 것    
    최근 OpenAPI (누구나 사용할 수 있도록 공개된 API : 구글 맵, 공공 데이터 등), 마이크로 서비스(하나의 큰 애플리케이션을 여러 개의 작은 애플리케이션으로 쪼개어 변경과 조합이 가능하도록 만든 아키텍쳐)등을 제공하는 업체 대부분은 REST API를 제공.