# 다형성(polymorphism)
- 하나의 객체가 여러 가지 타입을 가질 수 있는 것을 의미한다.   
- 자바에서는 이러한 다형성을 부모 클래스 타입의 참조 변수로 자식 클래스 타입의 인스턴스를 참조할 수 있도록하여 구현하고 있다.   
- 다형성은 상속, 추상화와 더불어 객체 지향 프로그래밍을 구성하는 중요한 특징 중 하나이다.

### 참조 변수의 다형성
- 자바에서는 다형성을 위해 부모 클래스 타입의 참조 변수로 자식 클래스 타입의 인스턴스를 참조할 수 있도록 하고 있다.
- 이때 참조 변수가 사용할 수 있는 멤버의 개수가 실제 인스턴스의 멤버 개수보다 같거나 적어야 참조할 수 있다.

```java 
예)
class Parent { ... }

class Child extends Parent { ... }

...

Parent pa = new Parent(); // 허용

Child ch = new Child();   // 허용

Parent pc = new Child();  // 허용

Child cp = new Parent();  // 오류 발생.
```

- 하지만 반대의 경우인 자식 클래스 타입의 참조 변수로는 부모 클래스 타입의 인스턴스를 참조할 수 없다.

- 참조 변수가 사용할 수 있는 멤버의 개수가 실제 인스턴스의 멤버 개수보다 많기 때문이다.

### instanceof 연산자

- 이러한 다형성으로 인해 런타임에 참조 변수가 실제로 참조하고 있는 인스턴스의 타입을 확인할 필요성이 생긴다.   
- 자바에서는 instanceof 연산자를 제공하여, 참조 변수가 참조하고 있는 인스턴스의 실제 타입을 확인할 수 있도록 해준다.
