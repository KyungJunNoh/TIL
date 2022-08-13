# 코루틴 (coroutine)

### 1. 코루틴 간단 예제
```kt
fun main() = runBlocking {
    launch {
        delay(1000L)
        println("World!") // "World!"
    }
    println("Hello") // 메인 루틴은 코루틴(서브루틴)이 실행되는 동안 실행
}
```

- ##### `runBlocking` : CoroutineScope 로 메인함수와 코루틴을 이어주는 코루틴 빌더, 서브루틴이 실행되고 있다면 메인 루틴이 끝나더라도 프로그램을 종료 하지 않도록 방지해주는 역할도 한다.
- ##### `launch` : 코루틴(서브루틴)을 하는 코루틴 빌더
- ##### `delay` : 특정 시간 동안 코루틴을 지연(일시 중단)

##### delay(1000L) 로 인하여 1초동안 작업이 지연되어 Hello, World! 가 출력된다.

<br>

### 2. 만약 runBlokcing 을 사용하지 않는다면 ?

```kt
fun main() {
    GlobalScope.launch {
        delay(1000)
        print("task 2")
    }
    print("task 1")
}
```

##### runBlocking 이 사용되지 않는다면 task 1 만 출력되고 프로그램이 종료되게 된다.

```kt
fun main() = runBlocking {
    launch {
        delay(1000)
        println("task 2")
    }
    println("task 1")
}
```

##### 반면 위와 같이 runBlocking 을 사용한다면 task 1 이 실행되고 1초 뒤에 task 2 가 실행된 뒤 프로그램이 종료되게 된다.

<br>

### 3. launch 를 함수로 추출
```kt
fun main() = runBlocking { // CorutineScope
    launch { doWorld() }
    println("Hello")
}

// 작업이 지연 될 수 있는 함수
suspend fun doWorld() {
    delay(1000L)
    println("World!")
}
```

- ##### `suspend` : 함수 안에서 delay 함수를 사용할 때 꼭 써야되는 키워드

##### launch 블럭 안에서 코루틴을 사용하는 함수의 코드가 있다면 그 함수에 suspend 키워드를 필수로 붙여줘야한다. <br> 만약 다음과 같이 launch 코루틴 빌더를 생략한다면 에러가 발생하진 않지만, delay가 되는 코드는 생략된다.
```kt
fun main() = runBlocking {
    doWorld()
    println("Hello")
}

suspend fun doWorld() {
    delay(1000L) // launch 함수를 사용하지 않아 무시됨.
    println("World!")
}
```

<br>

### 4. coroutineScope 코루틴 빌더
```kt
fun main() = runBlocking {
    doWorld() // do World 작업을 수행 후 다음 작업을 수행한다.
    println("Done")
}

suspend fun doWorld() = coroutineScope { // this: CoroutineScope
    launch {
        delay(2000L)
        println("World 2")
    }
    launch {
        delay(1000L)
        println("World 1")
    }
    println("Hello")
}
```

- ##### `corutineScope` : runBlocking 과 비슷한 역할을 하는것같다. 특징으로는 함수에 suspend 키워드를 사용해야하며, launch 함수를 사용할 수 있다.

##### corutineScope 와 runBlocking의 성질은 비슷하다 공식문서에 나와있다. 하지만 그 차이점을 아직 이해하지 못했다. 
https://kotlinlang.org/docs/coroutines-basics.html#scope-builder


