# Entity,DTO,VO
### Entity
```
Entity 클래스는 실제 DataBase의 테이블과 1 : 1로 매핑 되는 클래스로,
DB의 테이블내에 존재하는 컬럼만을 속성(필드)으로 가져야 한다.
Entity 클래스는 상속을 받거나 구현체여서는 안되며, 테이블내에 존재하지 않는 컬럼을 가져서도 안된다.
```

### DTO
```
DTO(Data Transfer Object)는 데이터 전송(이동) 객체라는 의미를 가지고 있다. DTO는 주로 비동기 처리를 할 때 사용한다.
```
- 계층간 데이터 **교환을 위한 객체(Java Beans)** 이다.   
- **DB의 데이터를 Service나 Controller 등으로 보낼 때** 사용하는 객체를 말한다.   
- 즉, DB의 데이터가 Presentation Logic Tier로 넘어올때는 DTO로 변환되어 오고가는 것이다.   
- 로직을 갖고 있지 않는 순수한 데이터 객체이며, getter/setter 메서드만을 갖는다.   
- 또한 **Controller Layer에서 Response DTO 형태로 Client에 전달**한다.

### VO
```
VO(Value Object)는 말 그대로 값 객체라는 의미를 가지고 있다.
VO의 핵심 역할은 equals()와 hashcode() 를 오버라이딩 하는 것이다.
VO 내부에 선언된 속성(필드)의 모든 값들이 VO 객체마다 값이 같아야, 똑같은 객체라고 판별한다.
```

### DTO와 VO 차이점
- VO는 DTO와 동일한 개념이지만 **read only 속성**을 갖는다.   
- VO는 **특정한 비즈니스 값을 담는 객체**이고, DTO는 **Layer간의 통신 용도로 오고가는 객체**를 말한다.