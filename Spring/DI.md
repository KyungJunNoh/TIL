# DI ( Dependency Injection, 의존성 주입 )
- 의존성 주입은 필요한 객체를 직접 생성하는 것이 아닌 외부로부터 객체를 받아 사용하는 것이다.  
이를 통해 객체간의 결합도를 줄이고 코드의 재활용성을 높일 수 있다.   

### 의존성 주입의 3가지 방법
1. 생성자 주입(Constructor Injection)
- **3가지 의존성 주입중 가장 추천하는 방법**이다.   
해당 클래스를 생성할때 해당 클래스의 객체들에 그 **생성자로 주입**해주는 방법이다.      
`final` 키워드를 사용함으로써 **불변에 대한 안전함이 보장**되어있다.   
lombok 라이브러리를 활용하면 `@RequireArgsConstructor` 로 간단하게 사용할 수 있다.

2. 필드 주입(Field Injection) 
- Spring 프레임워크의 `@Autowired` 어노테이션을 활용한 주입 방식으로,   
방법이 매우 간단하지만 **프레임워크에 의존적**이고 객체지향적으로 좋지 않은 단점이 있습니다.   

3. 수정자 주입(Setter Injection) 
- `setter` 메소드를 이용하여 주입하는 방법으로,   
 대부분 의존관계 주입은 한번 일어나면 어플리케이션 종료시점까지 의존관계를 변경할 일이 거의 없지만   
**public 으로 열려**있는 `setter` 로 인하여 **언제 어디서든 변경될 위험성**이 있다.