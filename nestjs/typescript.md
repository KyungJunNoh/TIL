# TypeScript 
최근 NestJS 를 시작하면서 TypeScript에 대해 공부를 해야겠다고 생각했다.

내가 알고있는 TypeScript는 JavaScript의 상위 호환인 언어로, 가장 큰 차이는 자바스크립트와는 다르게 정적타이핑(Number,Boolean,String 등..)을 제공하여 자료형이 다르다면 컴파일 시점에서 오류를 파악할 수 있고 코드의 가독성이 올라가는 장점이 있다.

내가 알고있는 TypeScript의 정보는 이 정도 이며, 더 자세히 알아보았다.

### TypeScript 란?
- MS 에서 **개발/관리되고 있는 오프소스 프로그래밍 언어**이다.
- **대규모 애플리케이션을 개발하는 데 자바스크립트가 어렵고 불편하다는 불만**에 대응하기 위해 개발되었다.
- TypeScript는 ES5의 Superset이므로 기존의 자바스크립트(ES5) 문법을 그대로 사용할 수 있다.
- ES6의 새로운 기능들을 사용하기 위해 Babel과 같은 별도 트랜스파일러(Transpiler)를 사용하지 않아도 ES6의 새로운 기능을 기존의 자바스크립트 엔진(현재의 브라우저 또는 Node.js)에서 실행할 수 있다.

### TypeScript의 장점
> TypeScript를 사용하는 가장 큰 이유는 정적 타입을 지원하는 것이다.

자바스크립트에서의 함수
```js
function sum(a, b) {
  return a + b;
}
```

이렇게 되면 파라미터의 형식이 정해지지 않아서 **어떤 타입의 반환값을 리턴해야 하는지 명확하지 않다.**

```js
sum(10, 20); // 30
```

```js
sum('10', '20'); // 1020
```

하지만 TypeScript 에서 정적 타이핑을 사용하여 다시 사용하고 String 타입으로 파라미터 값을 넘겨주면 오류가 난다.
```ts
function sum(a: number, b: number) {
  return a + b;
}
```
```ts
error TS2345: Argument of type '"10"' is not assignable to parameter of type 'number'.
```

다음과 같이 사용했을때 컴파일 시점에서 타입이 다르다며 에러가 난다.

또한 코드의 가독성을 높힐 수 있다.

### TypeScript를 공부하면서 느낀점
JS, TS를 많이 사용해보진 못했지만 JS는 정적 타이핑을 제공하지 않아서 협업을 할때, 타입이 달라져서 에러가 많이 날 것 같지만
정적 타이핑을 제공하는 TypeScript로 협업을 하면 타입이 달라서 나오는 오류는 만나지 않아서 협업을 하는데 시간이 단축 될 것 같다.