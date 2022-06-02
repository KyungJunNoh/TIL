### Math 클래스
Math 클래스는 수학에 필요한 메소드들을 모아둔 클래스이다.   
기본생성자를 만들 수 없게 되어있으며 모든 메소드가 static으로 정의되어있다.

정의되어있는 메소드들이 너무 많기에 자주 쓰이는 메소드들만 정리하겠다.

### 자주 사용되는 메소드

> static double random()
- 0.0 이상 1.0 미만의 범위에서 임의의 double형 값을 하나 생성하여 반환한다.

> static double abs(double a)   
> static double abs(float a)   
> static double abs(int a)   
> static double abs(long a)
- 전달된 값이 음수이면 그 값의 절댓값을 반환하며, 전달된 값이 양수이면 인수를 그대로 반환함.

> static double ceil(double a)	
- 전달된 double형 값의 소수 부분이 존재하면 소수 부분을 무조건 올리고 반환함.

> static double floor(double a)	  
- 전달된 double형 값의 소수 부분이 존재하면 소수 부분을 무조건 버리고 반환함.

> static long round(double a)   
> static int round(float a)
- 전달된 값을 소수점 첫째 자리에서 반올림한 정수를 반환함.

> static double rint(double a)	   
- 전달된 double형 값과 가장 가까운 정수값을 double형으로 반환함.

> static double max(double a, double b)   
> static float max(float a, float b)   
> static long max(long a, long b)
> static int max(int a, int b)
- 전달된 두 값을 비교하여 큰 값을 반환함.

> static double min(double a, double b)   
> static float min(float a, float b)   
> static long min(long a, long b)   
> static int min(int a, int b)
- 전달된 두 값을 비교하여 작은 값을 반환함.

> static double pow(double a, double b)	
- 전달된 두 개의 double형 값을 가지고 제곱 연산을 수행하여, ab을 반환함.

> static double sqrt(double a)	
- 전달된 double형 값의 제곱근 값을 반환함.

> static double sin(double a)   
> static double cos(double a)   
> static double tan(double a)   
- 전달된 double형 값에 해당하는 각각의 삼각 함숫값을 반환함.
