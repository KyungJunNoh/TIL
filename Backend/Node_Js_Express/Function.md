# Node.js - Function (함수)

## 지역변수
~~~
function localNum() {

    var num = 10; // 지역 변수 num에 숫자 10을 대입함.

    document.write("함수 내부에서 변수 num의 타입은 " + typeof num + "입니다.<br>"); // number

}

localNum();       // 함수 localNum()을 호출함.

document.write("함수의 호출이 끝난 뒤 변수 num의 타입은 " + typeof num + "입니다."); // undefined
~~~

## 전역 변수

~~~
var num = 10; // 전역 변수 num을 선언함.

function globalNum() {

    document.write("함수 내부에서 변수 num의 값은 " + num + "입니다.<br>"); // 10

    num = 20; // 전역 변수 num의 값을 함수 내부에서 변경함.

}

globalNum();  // 함수 globalNum()을 호출함.

document.write("함수의 호출이 끝난 뒤 변수 num의 값은 " + num + "입니다."); // 20
~~~
-> 함수 밖에서 변수를 선언했을때 전역변수가 되어 함수 내에서 num의 값을 바꾸면 밖에서도 적용이 된다.
~~~
function globalNum() {

    num = 10; // var 키워드를 사용하지 않고 변수 num을 선언함.

    document.write("함수 내부에서 변수 num의 값은 " + num + "입니다.<br>"); // 10

}

globalNum();  // 함수 globalNum()을 호출함.

document.write("함수의 호출이 끝난 뒤 변수 num의 값은 " + num + "입니다."); // 10
~~~
-> 함수 내에서 var 키워드를 사용하지 않고 선언하였을때 전역변수가 된다.

~~~
var num = 10; // 전역 변수 num을 선언함.

function globalNum() {

    var num = 20; // 같은 이름의 지역 변수 num을 선언함.

    document.write("함수 내부에서 변수 num의 값은 " + num + "입니다.<br>"); // 20

}

globalNum(); // 함수 globalNum()을 호출함.

document.write("함수의 호출이 끝난 뒤 변수 num의 값은 " + num + "입니다."); // 10
~~~
-> 함수밖에서 var num을 선언하고 함수 내에서 var num을 선언했을때 함수에서는 지역변수가 우선이되고 함수밖에선 전역변수가 우선이된다.
~~~
var num = 10; // 전역 변수 num을 선언함.

function globalNum() {

    var num = 20; // 같은 이름의 지역 변수 num을 선언함.

    document.write("함수 내부에서 지역 변수 num의 값은 " + num + "입니다.<br>");

    document.write("함수 내부에서 전역 변수 num의 값은 " + window.num + "입니다.<br>");

}

globalNum(); // 함수 globalNum()을 호출함.
~~~
-> 함수 안에 지역변수가 선언되있을때 함수밖의 전역변수를 사용하고싶다면 window.num 이라는 window 키워드를 사용하면 된다.


## 함수의 유효 범위
## 전역변수
```
<!DOCTYPE html>
<html lang="ko">

<head>
	<meta charset="UTF-8">
	<title>JavaScript Function Scope</title>
</head>

<body>

	<h1>함수의 유효 범위</h1>

	<script>
		// x, y를 전역 변수로 선언함.
		var x = 10, y = 20;

		// sub()를 전역 함수로 선언함.
		function sub() {
			return x - y;		// 전역 변수인 x, y에 접근함.
		}
		document.write("전역 함수에서 x - y의 값은 " + sub() + "입니다.<br>");

		// parentFunc()을 전역 함수로 선언함.
		function parentFunc() {
			var x = 1, y = 2;	// 전역 변수와 같은 이름으로 선언하여 전역 변수의 범위를 제한함.

			function add() {	// add() 함수는 내부 함수로 선언됨.
				return x + y;	// 전역 변수가 아닌 지역 변수 x, y에 접근함. 만약 전역변수로 접근하고싶다면 [window.x + window.y] 를사용하면 된다.
			}
			return add();
		}
		document.write("내부 함수에서 x + y의 값은 " + parentFunc() + "입니다.<br>");
	</script>
	
</body>

</html>
```