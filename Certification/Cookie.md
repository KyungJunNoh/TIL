# 쿠키(Cookie)
### 클라이언트 (브라우저 or 디바이스) 로컬에 저장되는 'key-value'쌍의 데이터파일

[ 특징 ]     

- 쿠키 유효시간을 명시 가능 / 브라우저가 종료되어도 유지됨
- 클라이언트에 저장했다가 참조
- 최대 300개 / 하나의 도메인당 20개 까지 / 하나의 쿠키는 4KB까지 가능
- Response header에 Set-Cookie 속성을 사용하면 쿠키를 만들 수 있음
- 사용자가 따로 처리 안해도 HTTP가 Request시 header에 자동으로 넣음


[ 구성요소 ]

1) 이름 : 각각의 쿠키를 구별하는데 사용되는 이름
2) 값 : 쿠키의 이름과 관련된 값
3) 유효시간 : 쿠키의 유지시간
4) 도메인 : 쿠키를 전송할 도메인
5) 경로 : 쿠키를 전송할 요청 경로

 
[동작 방식]

1. 클라이언트가 HTTP Request 를 서버에게 보냄
2. 서버에서 유효성(회원인지)확인 후 쿠키를 생성 & HTTP Response 헤더에 쿠키 넣어 응답
3. 클라이언트는 HTTP Response의 header에서 쿠키를 추출하여 저장
4. 클라이언트가 Request하고 싶을 때, HTTP가 해당 쿠키를 찾아 header에 자동으로 넣어서 전송

[ LifeCycle ]

- 쿠키 유효 시간이 만료되면 종료
- 브라우저 재시작 해도 종료되지 않음
- 유효시간 만료되도 클라이언트에 쌓임 (그래서 주기적으로 삭제 필요)

 
[ 사용 예시 ]

- 팝업창 다시보지 않기
- 아이디 / 비밀번호 저장
- 장바구니