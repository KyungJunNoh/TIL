# Parameter (매개변수)
- 자바스크립트에서는 함수를 정의할 때는 매개변수의 타입을 따로 명시하지 않습니다.
함수를 호출할 때에도 인수(argument)로 전달된 값에 대해 어떠한 타입 검사도 하지 않습니다.
함수를 호출할 때 함수의 정의보다 적은 수의 인수가 전달되더라도, 다른 언어와는 달리 오류를 발생시키지 않습니다. 이 같은 경우 자바스크립트는 전달되지 않은 나머지 매개변수에 자동으로 undefined 값을 설정합니다.
```
매개변수(parameter)란 함수의 정의에서 전달받은 인수를 함수 내부로 전달하기 위해 사용하는 변수를 의미합니다.

인수(argument)란 함수가 호출될 때 함수로 값을 전달해주는 값을 말합니다.
```
## 예제
~~~
function addNum(x, y, z) { // x, y, z라는 3개의 매개변수를 가지는 함수 addNum()을 정의함.

    return x + y + z;

}

addNum(1, 2, 3); // 인수로 1, 2, 3을 전달하여 함수를 호출함. -> 6

addNum(1, 2);    // 인수로 1, 2을 전달하여 함수를 호출함. -> NaN

addNum(1);       // 인수로 1을 전달하여 함수를 호출함. -> NaN

addNum();        // 인수로 아무것도 전달하지 않고 함수를 호출함. -> NaN
~~~
 위의 예제에서 addNum() 함수를 호출할 때 인수가 세 개보다 적게 전달되면, 계산할 수 없다는 의미인 NaN을 반환합니다.

그 이유는 전달되지 않은 나머지 값이 자동으로 undefined 값으로 설정되어, 산술 연산을 수행할 수 없기 때문입니다.

하지만 다음 예제처럼 하면 NaN을 반환하지 않고 전달된 인수만을 가지고 정상적으로 계산하는 함수를 작성할 수 있습니다.

~~~
function addNum(x, y, z) {

    if(x === undefined) // 함수 호출시 x에 해당하는 인수가 전달되지 않은 경우

        x = 0;          // 변수 x의 값을 undefined에서 0으로 변경함.

    if(y === undefined) // 함수 호출시 y에 해당하는 인수가 전달되지 않은 경우

        y = 0;          // 변수 y의 값을 undefined에서 0으로 변경함.

    if(z === undefined) // 함수 호출시 z에 해당하는 인수가 전달되지 않은 경우

        z = 0;          // 변수 z의 값을 undefined에서 0으로 변경함.

    return x + y + z;

}

addNum(1, 2, 3); // 6

addNum(1, 2);    // 3

addNum(1);       // 1

addNum();        // 0
~~~

## 디폴트 매개변수와 나머지 매개변수

### 디폴트 매개변수
~~~
function mul(a, b = 1) { // 인수가 한 개만 전달되면 나머지 매개변수의 값을 언제나 1로 설정해 줌.

    return a * b;

}

mul(3, 4); // 12

mul(3);    // 3
~~~
선언부터 b의 값을 초기화시켜주면 값이 한개만 들어왔을때 알아서 3 과 1을 곱함