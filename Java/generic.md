# 제네릭(generic)
- 데이터의 타입(data type)을 일반화한다(generalize)는 것을 의미한다.
- 클래스나 메소드에서 사용할 내부 데이터 타입을 컴파일 시에 미리 지정하는 방법이다.
- 이렇게 컴파일 시에 미리 타입 검사(type check)를 수행하면 다음과 같은 장점을 가진다.
### 제네릭의 선언 및 생성
- 자바에서 제네릭은 클래스와 메소드에서 다음과 같은 방법으로 선언이 가능하다.
```
예)

class MyArray<T> {
    T element;
    void setElement(T element) { this.element = element; }
    T getElement() { return element; }
}
```
- 위의 예제에서 사용된 'T'를 타입 변수(type variable)라고 하며, 임의의 참조형 타입을 의미한다.
- 꼭 'T'뿐만 아니라 어떠한 문자를 사용해도 상관없다. 여러 개의 타입 변수는 쉼표(,)로 구분하여 명시할 수 있다.
- 타입 변수는 클래스에서뿐만 아니라 메소드의 매개변수나 반환값으로도 사용할 수 있다.

