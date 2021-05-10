# 20-12-01(변수의scope와 객체)
### 1 . 아래가 의도하지 않은 결과를 나타내는 이유를 설명하시오.

```java
char ch = '가';
System.out.println(ch + '\n');
```

- 현재 '가'와 '\n'은 char타입으로 지정되었고, char는 int보다 낮은 데이터 값을 가지고 있기 때문에  int형으로 자동 형변환이 되어 연산을 진행한다. 그래서 서로의 유니코드 값이 인코딩 되어 연산된 값인 정수 44042로 나온다. 의도한대로 결과를 얻기 위해서는 '\n'을 "\n"으로 바꿔줘야 된다.

---

### 2. 변수의 scope는?

> scope

1. 변수의 대한 접근과 변수가 존재 할 수있는 영역을 말한다.
2. 중괄호 {}로 한 영역이 생성된다면 그 영역에 관한 스코프를 형성한다.
3. 프로그램 상에서 사용되는 변수들은 사용가능한 범위를 가진다. 

scope 예시

![변수의 스코프](https://user-images.githubusercontent.com/75012998/102714298-f5f5da80-4310-11eb-9438-a0d314f9c367.jpg)

---

### 3. 지역변수는?

- {}안에 생성되어 사용할 수있는 변수이다.

지역변수의 예

![지역변수](https://user-images.githubusercontent.com/75012998/102714306-fc845200-4310-11eb-9e3e-c25d6fd98b59.jpg)

---

### 4.펙토리얼을 구하는 재귀 함수를 만드시오.

```java
public class Factorial{

    public static void main(String[] args){
	     System.out.println("3 factorial : " +  factorial(3));
	     System.out.println("12 factorial : " + factorial(12));
	}//main end
  
	 //재귀호출의 흐름
	   public static int factorial(int n) {
		    if(n == 1) {
			    return 1;
		    }else {
			    return n* factorial(n-1);
		    } // if end
        
	    } // factorial end
      
} // class end
```

> 재귀함수

1. 메소드 내에서 자기 자신을 특정한 조건이 될 때까지 호출 하는 함수

재귀함수의 흐름의 예

![재귀함수흐름](https://user-images.githubusercontent.com/75012998/102714311-027a3300-4311-11eb-8fab-63a38854045a.jpg)

---

### 5.클래스의 구성요소는 무엇인가?

- 데이터(변수) : 프로그램상에서 유지하고 관리해야할 데이터
- 기능(함수) : 데이터를 처리하고 조작하는 기능

---

### 6.원의 넓이는 구하는 프로그램을 아래와 같이 작성하시오.

```java
-원클래스를 만들것

-메인 메소드를 가진 다른 클래스에서 원 객체를 생성할것
```

답 : 

- Class 소스코드

    ```java
    class Circle{
    	double radius;
    	
    	public void setCircle(double radius){
    		this.radius = radius;
    	}
    	public double getCircle(){
    		return radius * radius * Math.PI;
    	}
    }
    ```

- Main 소스코드

    ```java
    class Circle{
    	public static void main(String[] args){
    		Circle circle = new Circle();
    		circle.setCircle(10);
    		System.out.println("원의 넓이 : " + circle.getCircle());
    	}
    }
    ```

---

### 7. 객체란 무엇인가?

1. 소프트웨어 세계에서 구현될 대상
2. 메인 클래스에서 기존에 선언한 클래스를 참조할 때 생성자를 통해 해당 크기만큼 메모리를 할당하는 공간적인 개념.

---

### 8. 아래의 클래스에 대하여, 메모리 그림을 그리시오.

```java
Rectangle rec = new Rectangle();
 
public class Rectangle {
	int height;
	int width;
	
	public int getHeight() {
		return height;
	}
	
	public void setHeight(int height) {
		this.height = height;
	}
	
	public int getWidth() {
		return width;
	}
	
	public void setWidth(int width) {
		this.width = width;
	}
	
	public int getArea() {
		return width * height;
	}
	
}
```

![8번문제](https://user-images.githubusercontent.com/75012998/103089313-f5bb4f00-4630-11eb-9c9c-075947fad364.jpg)

---

### 9.클래스와 객체의 차이는 무엇인가?

> class

- 객체를 정의 해놓은 것 또는 객체의 틀, 설계도라 할 수 있다.
- 객체를 생성하는데 사용된다.

> object

- 소프트웨어 세계에서 구현될 대상
- 클래스에 정의된 내용대로 메모리가 생성된 것이다.

클래스와 객체 예

![클래스와 객체](https://user-images.githubusercontent.com/75012998/102714322-1160e580-4311-11eb-82a7-d7e43383c595.png)

---

### 10.아래의 프로그램을 작성하시오.

```java
- 1 부터 num 까지 합을 구하는 class를 작성하도록 하시오.
```

- Class 소스코드

    ```java
    class TestMain{
    	int num;

    	TestMain(int num){
    		this.num = num;
    	}
    	public void print() {
    		int total = 0;
    		for(int i=1 ; i <= num ; i++) {
    			total += i;
    			System.out.println("1부터 num까지의 합 : " + total);
    		}
    	}
    }
    ```

- Main 소스코드

    ```java
    public class TestMain {
    	public static void main(String[] args) {
    		TestMain test = new TestMain(100);
    		test.print();
    	}
    }
    ```

---

### 11.아래의 클래스를 작성하시오.

```java
StraPrint strPrint = new StarPrint();

strPrint.printTriangle(3); 
System.out.println();
strPrint.printReverseTriangle(3); 
===============================
*
**
***

***
**
*
```

- Class 소스코드

    ```java
    public class StarPrint {
    	
    	public void printTriangle(int num) {
    		for(int i=1 ; i <= num ; i++) {
    			for(int j=1 ; j <= i ; j++) {
    				System.out.print('*');
    			}
    			System.out.println(" ");
    		}
    	}
    	
    	public void printReverseTriangle(int num) {
    		for(int i=1 ; i <= num ; i++) {
    			for(int j=i ; j <= num ; j++) {
    				System.out.print('*');
    			}
    			System.out.println(" ");
    		}
    	}

    }
    ```

- Main 소스코드

    ```java
    public class TestMain {
    	
    	public static void main(String[] args) {
    		StarPrint strPrint = new StarPrint();

    		strPrint.printTriangle(3); 
    		System.out.println();
    		strPrint.printReverseTriangle(3); 
    	}	
    }
    ```

---

### 12.아래의 프로그래밍을 작성하시오.

```java
Gugudan gugudan = new Gugudan();
gugudan.printGugu(10);  //1단부터 10단까지 출력
gugudan.printGugu(20);  //1단부터 20단까지 출력
```

- Class 소스코드

    ```java
    public class Gugudan {

    	public void printGugu(int num) {
    		for(int i=1 ; i <= num ; i++) {
    			System.out.println(i + "단 출력");
    			for(int j=1 ; j <= 9 ; j++) {
    				System.out.println(i + "x" + j + "=" + (i*j));
    			}
    		}
    	}
    }
    ```

- Main 소스코드

    ```java
    public class TestMain {
    	
    	public static void main(String[] args) {
    		Gugudan gugudan = new Gugudan();
    		gugudan.printGugu(10);  //1단부터 10단까지 출력
    		gugudan.printGugu(20);  //1단부터 20단까지 출력 
    	}	
    }
    ```

---

### 13. 아래의 BankAccount 객체에 대하여 그림을 그리시오.

![14번문제](https://user-images.githubusercontent.com/75012998/103089321-fbb13000-4630-11eb-8a63-9e28e529c952.jpg)

