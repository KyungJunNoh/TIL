# Business Logic
- 비즈니스 로직이란 만약 영역을 두개로 나눴을때 
- 중복 아이디가 있는지 없는지를 검사하기 위한 일련의 과정들 (1번째 영역)
- 나머지는, 유저에게 단순히 텍스트나 다이얼로그로 알려주는 것이 있다. (2번째 영역)
- 첫번째 영역에서의 코딩을 흔히, 비즈니스 로직이라 부른다. 위의 아이디 중복찾기를 다시 예시로 들자면, 아래와 같은 비즈니스 로직이 작성될 것이다.
```
회원이 작성한 아이디 값 저장하기 -> 회원정보가 있는 데이터베이스 연결 ->

데이터베이스에 회원이 작성한 아이디 값이 있는지 Select -> 

회원의 아이디가 이미 있는지 없는지 여부를 데이터화 하여 저장 -> 

데이터베이스 연결 끊기 -> View영역에게 가공된 데이터 전달
```

- 이러한 비즈니스 로직은 유저 눈엔 보이진 않지만, 유저가 바라는 결과물을 올바르게 도출하기 위해 코드로 짜여진다.   
즉, 프로그래머는 유저가 원하는 행위를 컴퓨터에게 잘 전달하기 위해서는 비즈니즈 로직을 잘 구상해야 한다는 의미이다.   
이처럼, 비지니스 로직은 프로그래밍에서 빠질 수 없는 요소이며, 응용 프로그램의 핵심이 된다.