# Path Variable 과 Query Parameter

### Query Parameter
GET 메소드를 사용하여 데이터를 전송할 때 URL 에 QueryParameter 을 사용하여 서버로부터 데이터를 받을 수 있다.

```url
ex) https://localhost:8080/v1/users?id=123 // 아이디가 123인 사용자를 가져온다.
```


### Path Variable
Query Parameter 와는 다른 방법으로 Path Variable을 사용할 수도 있다.
```url
ex) https://localhost:8080/v1/users/123 // 아이디가 123인 사용자를 가져온다.
```

### Path Variable과 Query Parameter는 언제 사용하면 좋을까?

어떤 **resource 를 식별** 하고 싶으면 **Path Variable 을 사용**하고,   
**정렬이나 필터링**을 해야한다면 **Query Parameter**를 사용하는 것이 좋다.

```url
https://localhost:8080/v1/users // 사용자 목록을 가져온다.
https://localhost:8080/v1/users?occupation=programer // 프로그래머인 사용자 목록을 가져온다.
https://localhost:8080/v1/users/123 // 아이디가 123인 사용자를 가져온다.
```

쉽게말해 Path Variable 은 단일 조회,  
Query Parameter 는 단체 조회, 특정 조건이 걸린 것들을 조회해올 때 사용하면 좋다.

### 정리

위에 처럼 개발을 하지 않아도 개발은 되지만, RESTful 하지않아 개발속도에 영향을 미칠 수 있다.

