# 코틀린 공식문서 정리

# 1. 소개

## HelloWorld

```kotlin
package org.kotlinlang.play         // 1

fun main() {                        // 2
    println("Hello, World!")        // 3
}
```

1. 코틀린은 패키지를 사용할 수 있으며 패키지를 사용하지 않으면 기본 패키지로 지정이 된다.
2. 코틀린은 main 함수가 있다. Kotlin 1.3 버전부터는 파라미터 없이 main 함수를 선언할 수 있다.
3. 코틀린의 `println(”문자열”)` 은 자바의 `System.out.println(”문자열”);` 과도 같이 문자열을 출력할 수 있다. 또한 **코틀린은 세미콜론이 선택사항**이다.

코틀린의 1.3 버전 아래는 main 함수의 매개변수에 `Array<String> 타입`을 가진 변수를 가져야한다.

```kotlin
fun main(args: Array<String>) {
    println("Hello, World!")
}
```

# 함수

### 기본 매개 변수 값 및 명명된 인수

```kotlin
fun printMessage(message: String): Unit {                               // 1
    println(message)
}

fun printMessageWithPrefix(message: String, prefix: String = "Info") {  // 2
    println("[$prefix] $message")
}

fun sum(x: Int, y: Int): Int {                                          // 3
    return x + y
}

fun multiply(x: Int, y: Int) = x * y                                    // 4

fun main() {
    printMessage("Hello")                                               // 5                    
    printMessageWithPrefix("Hello", "Log")                              // 6
    printMessageWithPrefix("Hello")                                     // 7
    printMessageWithPrefix(prefix = "Log", message = "Hello")           // 8
    println(sum(1, 2))                                                  // 9
    println(multiply(2, 4))                                             // 10
}
```

1. String 유형의 매개변수를 사용하여 Unit(즉,반환 값 없음)을 반환하는 간단한 함수이다. ( 자바에서는 void 를 의미하는것 같음. 생략 가능한 키워드이다. )
2. 기본값이 Info인 두 번째 **선택적(Optional) 매개변수**를 사용하는 함수이다.
3. 이 함수는 Integer 자료형의 값을 반환하는 함수이다.
4. 이 함수는 3번과 같이 단순히 값을 반환할때 축약할 수 있는 형식의 함수이다. (single-expression function)
5. Hello 인수를 활용하여 Hello를 출력할 수 있게한다.
6. 두 매개 변수로 함수를 호출하여 두 매개 변수 모두에 대한 값을 전달한다.
7. 두 번째 함수를 제외한 동일한 함수를 호출한다. 기본 값인 Info 를 사용한다.
8. 매와수변수와 인수 순서를 변경하여 동일한 함수를 호출한다.

(명명 인수 공식문서 : [https://kotlinlang.org/docs/functions.html#named-arguments](https://kotlinlang.org/docs/functions.html#named-arguments))

1. 합계 함수 호출의 결과를 출력한다.
2. 곱셈 함수 호출의 결과를 출력한다.

### 인픽스 함수 (중위 표기법)

단일 매개 변수를 가진 멤버 함수와 확장자를 infix 함수로 변환할 수 있다.