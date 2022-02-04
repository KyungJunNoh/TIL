# 백엔드 기술 면접

**1. 컴포넌트와 모듈의 차이**
> 모듈과 컴포넌트는 비슷하지만 모듈이 컴포넌트보다 큰 단위라고 생각합니다.
> 
> 컴포넌트는 하나의 부품입니다. 보통 작은 영역에서 서로 연관되어 있고 다용도로 사용이 가능하게 만듭니다. UI를 제어하는 타이머같은 Back단에서 스레드를 보조하는 컴포넌트로 예를 들 수 있습니다.
> 모듈은 조금 작은 범위의 조각입니다. 외부 인터페이스가 없는 복합적인 수요기능에서 실행될 수 있는 단위 입니다. 
> 
> 데이터베이스나 이메일 같은 통합적인 기능을 제공하면서 라이브러리처럼 사용될 수 있는 것들 입니다. 그리고 호환성이 더 좋습니다.


**2. 자바란 무엇인가**
> 자바는 객체지향프로그래밍 언어로서 보안성이 뛰어나며 컴파일한 코드는 다른 운영체제에서 사용될 수 있도록 클래스(.class 파일)로 제공됩니다. C++언어의 객체지향적인 장점을 살리면서 분산환경을 지원해 효율적입니다.

**3. 자바의 구동원리**
> 자바로 작성한 코드는 [.java]라는 확장자를 가지며 자바에 존재하는 javac라는 전용컴파일러가 [.java]로 끝나는 자바코드를 컴퓨터가 이해할 수 있도록 프로그래밍 언어로 기계어로 변경하게 되면 [.class]라는 확장자를 가진 파일이 생성되는데 [.class]파일은 JVM을 통해서 실행하게 됩니다.

**4. JVM의 특징**
> 자바 가상머신(Java Virtual Machine) 이라 불리며 자바소스로부터 만들어진 바이너리파일 즉 [.class]파일을 실행하기 위해 필요합니다.
>
> java가 OS에 구애받지 않고 재사용가능하게 해줍니다. 그리고 자동메모리 관리기법인 Grabage Collection을 수행합니다.
>
> + JRE : 자바실행환경. JVM으로 자바프로그램을 동작시킬 때 필요한 파일들을 가지고 있습니다.
> + JDK : Java를 개발하기 위해 필요한 환경입니다. JDK에는 JRE가 포함되어 있습니다.

**5. 객체지향과 절차지향의 차이점**
> 절차지향 프로그래밍이란 물이 위에서 흐르는 것과 같이 순차적인 처리가 중요시되며 프로그램 전체가 유기적으로 연결되도록 만드는 프로그래밍 기법입니다. 컴퓨터의 처리구조와 유사해 실행속도가 빠르다는 장점이 있습니다. 반면 유지보수가 어렵고 실행순서가 정해져있어 코드의 순서가 바뀌면 결과값이 달라질 수 있고 디버깅이 어렵다는 단점이 있습니다.
>
> 객체지향은 실제세계를 모델링하여 소프트웨어를 개발하는 방법입니다. 마치 컴퓨터 부품을 하나씩 사다가 컴퓨터를 조립하는 것과 같은 방법입니다. 코드의 재활용성이 높고 디버깅이 쉬운 장점이 있으며 처리속도가 절차지향보다 느리고 설계에 많은 시간이 소요되는 단점이 있습니다.

**6. 객체지향 언어의 특징**
> - 캡슐화 : 관련된 데이터와 알고리즘이 하나의 묶음으로 정리된 것으로써 데이터를 감추고 외부세계와는 메소드를 통해 상호작용 합니다.
>
> - 상속 : 이미 작성된 클래스를 이어받아 새로운 클래스를 생성하는 기법으로 기존 코드를 재활용해서 사용합니다.
>
> - 다형성 : 하나의 이름으로 많은 방법에 대처하는 기법입니다.

**7. 상속과 구현의 차이점과 특징 및 장단점**

**8. 오버라이딩과 오버로딩의 차이점과 특징**
> 오버로딩은 '많은 것을 싣는다.', 오버라이딩은 '재정의한다'는 사전적인의미를 가진 만큼 차이점도 이와 비슷하다고 볼 수 있습니다.
> 
> 오버로딩은 하나의 클래스 안에서 인스턴스 개수나 형식이 다른 동일한 이름의 메소드를 여러개 정의하는 것이고 정적 바인딩 입니다.
> 
> 오버라이딩은 상속을 했을 경우에 적용할 수 있고, 기존의 내용에 틀만 가져와서 재정의 하는 것이고 동적 바인딩 입니다. 

**9. 기본형 변수와 참조형 변수는 무엇일까?**
> 자바가 제공하는 기본 변수는 총 8가지로 char,byte,short,bollean,int,long,float,double 이 있습니다.
> 
> 참조형은 값이 저장된 곳의 메모리 주소를 저장하는 공간으로 객체의 주소를 저장합니다. 자바에서 기본형 변수 8가지를 제외하고는 모두 참조형 입니다.

**10. 스택 오버플로우가 왜 일어나는가?**
> 스택포인터가 스택의 경계를 넘어 설 때 일어납니다. 호출 스택은 제안된 양의 주소공간을 이루며 프로그램 시작 시 결정됩니다.