### Reflection 이란?
구체적인 클래스 타입을 알지 못해도 그 클래스의 **메소드, 타입, 변수들에 접근할 수 있도록 해주는 자바 API**

ex) 1. 런타임에 지금 실행되고 있는 클래스를 가져와서 실행해야하는 경우    
2. 동적으로 객체를 생성하고 메서드를 호출하는 방법   
3. IntelliJ 에서 자동완성 기능   
4. 스프링 어노테이션 자동완성

자바의 리플렉션은 **클래스, 인터페이스, 메소드들을 찾을 수 있고, 객체를 생성하거나 변수를 변경하거나 메소드를 호출**할 수 있다.

### Method를 활용하여 클래스 반환 방법
- class.getSuperClass() : 슈퍼 클래스를 반환
- class.getDeclaredClass() : 명시적으로 선언된 모든 클래스 및 인터페이스, 열거형을 반환
- class.getDeclaringClass() : 클래스에 구성된 클래스(명시적으로 선언된)를 반환합니다.
- class.getEnclosingClass() : 클래스의 즉시 동봉된 클래스를 반환합니다.

### Reflection 의 특징
- `확장성` : 애플리케이션은 정규화된 이름을 사용하여 확장성 객체의 인스턴스를 생성하여 외부 사용자 정의 클래스를 사용할 수 있다.
- `클래스 브라우저 및 시각적 개발 환경을 제공` : 클래스 브라우저는 클래스의 Method, Property, Constructor 를 열거할 수 있어야 한다. 시각적 개발 환경은 개발자가 올바른 코드를 작성하는데 도움이 되도록 Reflection에서 사용할 수 있는 형식 정보를 사용하면 도움이 된다.
- `디버거 및 테스트 도구이다.` : 디버거는 개인 Property, Method, Constructor 를 검사할 수 있어야 한다. 테스트 장치는 Reflection 을 사용하여 클래스에 정의된 발견 가능한 세트 API를 체계적으로 호출하여 테스트에서 높은 수준의 코드 커버리지를 보장한다.

### Reflection 의 주의사항 및 단점.
Reflection 은 강력한 도구이지만, 무분별하게 사용해서는 안된다. Reflection 을 사용하지 않고 수행 가능하다면, 사용하지 않는 것이 좋다. Reflection 을 통해 코드에 접근할때에는 다음 사항을 염두에 두어야 한다.

- `성능` : Reflection 에는 동적으로 해석되는 유형이 포함되므로, 특정 JVM 최적화를 수행할 수 없다. 따라서 Reflection 작업은 비 Reflection 작업보다 성능이 떨어지므로, 성능에 민감한 애플리케이션에서 자주 호출되는 코드엔 사용되지 않아야 한다.
- `보안 제한 사항` : Reflection 에는, 시큐리티 매니저의 실행 시에 존재하지 않는 실행 시 **액세스 권한**이 필요한다. 그러므로 제한된 보안 컨텍스트에서 실행되어야 하는 코드에 대한 중요한 고려사항 이다.
- `캡슐화를 저해` : Reflection private 한 Property 및 Method 에 액세스하는 것과 같이 비 Reflection 코드에서 작동하지 않는 코드를 수행할 수 있으므로, **Reflection 을 사용하면 예기치 않은 부작용이 발생하여 코드 기능이 저하되고 이식성이 손상**될 수 있다. 또한 Reflection 은 추상화를 깨뜨려 플랫폼 업그레이드 시 동작이 변경될 수 있다.