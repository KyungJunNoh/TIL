# Lombok의 @NoArgsConstructor, @AllArgsConstrouctor, @RequiredARgsConstrouctor

프로젝트 개발을 하면서 Lombok의 이해 없이 그냥 쓰고 넘어가는것같아서 정리한다.

> ### Lombok 이란?
 매번 반복되는 코드(생성자, Getter, Setter 등등..)을 ```Annotation``` 치환하여 자동으로 작성해주게 하는 Java 라이브러리 이다.

Lombok이 사용되는 경우는 주로 DTO나 Entity, 생성자 주입을 받을때 사용된다.

그리고 Lombok의 신기한점은 자바 코드에서 ```@Getter```를 사용했다면 컴파일이 된 .class 파일에서는 순수 자바 코드형태로 바뀐다는 점이다!

```java
// Code
class Person{
    @Getter
    @Setter
    private String name;
}
​
// Compiled
class Person {
    private String name;
​
    Person() {
    }
​
    public String getName() {
        return this.name;
    }
​
    public void setName(final String name) {
        this.name = name;
    }
}
```

이런식으로 말이다.

이번 편은 프로젝트를 하면서 내가 많이 부족했던 지식인, 생성자 관련 어노테이션인
```@NoArgsConstructor, @AllArgsConstrouctor, @RequiredARgsConstrouctor``` 이 어노테이션들에 중점에 마줘서 하기에 롬복에대한 설명은 여기까지 하겠다.

> ### @NoArgsConstructor

매개변수가 없는 생성자(기본 생성자)를 생성한다. 만약 불가능 하다면(final 필드 떄문에) 컴파일 에러가 난다. 만약 @NoArgsConstructor(force = true)를 사용하면 컴파일 에러를 발생시키는 대신 모든 final 필드는 기본값(0, false, null)로 초기화된다.

```java
@Getter 
@NoArgsConstrouctor
public class Store extends Common { 
    
    private String companyName; // 상호명
    private String industryTypeCode; // 업종코드
    private String businessCodeName; // 업태명 
    private String industryName; // 업종명(종목명) 
    private String telephone; // 전화번호 
    private String regionMoneyName; // 사용가능한 지역화폐 명 
    private boolean isBmoneyPossible; // 지류형 지역화폐 사용가능 여부 
    private boolean isCardPossible; // 카드형 지역화폐 사용가능 여부 
    private boolean isMobilePossible; // 모바일형 지역화폐 사용가능 여부 
    private String lotnoAddr; // 소재지 지번주소 
    private String roadAddr; // 소재지 도로명주소 
    private String zipCode; // 우편번호 
    private double longitude; // 경도 
    private double latitude; // 위도 
    private String sigunCode; // 시군 코드 
    private String sigunName; // 시군 이름 
    
    /* NoArgsConstructor를 통해 아래의 생성자를 자동 생성할 수 있다. 
    public Store() { 

    } 
    */
}
```

> ### @RequiredArgsConstrouctor

특정 필드만을 사용하는 생성자를 자동완성 시켜주는 어노테이션이다. 생성자의 인자로 ```@NonNull(Null이 아니여야하는 상태)``` 어노테이션을 붙여 해당 필드만을 인자로 추가할 수 있다. 아니면 해당 필드를 final로 선언해도 의존성 주입을 받을 수 있다.

아래의 코드로 예시를 들어 보겠다.
```java
@Getter 
@RequiredArgsConstrouctor
public class Store extends Common { 
    
    @NonNull
    private String companyName; // 상호명
    private final String industryTypeCode; // 업종코드
    private String businessCodeName; // 업태명 
    private String industryName; // 업종명(종목명) 
    private String telephone; // 전화번호 
    private String regionMoneyName; // 사용가능한 지역화폐 명 
    private boolean isBmoneyPossible; // 지류형 지역화폐 사용가능 여부 
    private boolean isCardPossible; // 카드형 지역화폐 사용가능 여부 
    private boolean isMobilePossible; // 모바일형 지역화폐 사용가능 여부 
    private String lotnoAddr; // 소재지 지번주소 
    private String roadAddr; // 소재지 도로명주소 
    private String zipCode; // 우편번호 
    private double longitude; // 경도 
    private double latitude; // 위도 
    private String sigunCode; // 시군 코드 
    private String sigunName; // 시군 이름 
    
    /* @RequiredArgsConstructor 통해 아래의 생성자를 자동 생성할 수 있다. 
    public Store(String companyName, String industryTypeCode) { 
        this.companyName = companyName; 
        this.industryTypeCode = industryTypeCode; 
    } 
    */

}
```

> ### @AllArgsConstrouctor
모든 필드에 대한 생성자를 만들어준다. 마찬가지로 @NonNull 필드에 대한 null check 구문을 생성해준다.

이해를 더 쉽게 하기위해 극단 적인 예로 아래 코드를 예시로 들어보겠다.
```java
@Getter 
@AllArgsConstructor 
public class Store extends Common { 
    private String companyName; // 상호명 private 
    String industryTypeCode; // 업종코드 private 
    String businessCodeName; // 업태명 
    private String industryName; // 업종명(종목명) 
    private String telephone; // 전화번호 
    private String regionMoneyName; // 사용가능한 지역화폐 명 
    private boolean isBmoneyPossible; // 지류형 지역화폐 사용가능 여부 
    private boolean isCardPossible; // 카드형 지역화폐 사용가능 여부 
    private boolean isMobilePossible; // 모바일형 지역화폐 사용가능 여부 
    private String lotnoAddr; // 소재지 지번주소 
    private String roadAddr; // 소재지 도로명주소 
    private String zipCode; // 우편번호 
    private double longitude; // 경도 
    private double latitude; // 위도 
    private String sigunCode; // 시군 코드 
    private String sigunName; // 시군 이름 
    
    /* @AllArgsConstructor를 통해 아래의 생성자를 자동 생성할 수 있다. 
    public Store(String companyName, String industryTypeCode, String businessCodeName, String industryName, String telephone, String regionMoneyName, boolean isBmoneyPossible, boolean isCardPossible, boolean isMobilePossible, String lotnoAddr, String roadAddr, String zipCode, double longitude, double latitude, String sigunCode, String sigunName) 
    { 
        this.companyName = companyName; 
        this.industryTypeCode = industryTypeCode; 
        this.businessCodeName = businessCodeName; 
        this.industryName = industryName; 
        this.telephone = telephone; 
        this.regionMoneyName = regionMoneyName; 
        this.isBmoneyPossible = isBmoneyPossible; 
        this.isCardPossible = isCardPossible; 
        this.isMobilePossible = isMobilePossible; 
        this.lotnoAddr = lotnoAddr; 
        this.roadAddr = roadAddr; 
        this.zipCode = zipCode; 
        this.longitude = longitude; 
        this.latitude = latitude; 
        this.sigunCode = sigunCode; 
        this.sigunName = sigunName; 
    } */ 
}
```
Store라는 엔티티 혹은 DTO 에 매개변수에 모든 필드를 담아야하는 
생성자를 만들어야하는데 Lombok이 없다면 주석과 같은 코드를 직접 짜야할 것이다. 
하지만 우리에게는 Lombok이라는 비장의 무기가 있어 코드의 가독성, 개발의 편의를 엄청나게 증진시킬 수 있다.

### Refrence By.
> https://www.korecmblog.com/lombok/#noargsconstructor   
> https://mangkyu.tistory.com/78