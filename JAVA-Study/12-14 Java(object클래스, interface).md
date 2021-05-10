#  20-12-14(object클래스, interface)
### 1. Object 클래스에 대하여 설명하시오.

> Object

- 모든 자바클래스의 최상위 부모클래스이다. 
- 상속하는 클래스가 없다면 컴파일러에 의해 java.lang.Object 클래스를 상속하게 코드를 구성.
- 함수 오버라이딩 하면 자식 함수가 호출된다.

---

### 2. 아래와 같이 출력 되는 이유를 설명하시오.

```java
class A {
	
	 @Override
	 public String toString() {
		
		 return "이것은 A 클래스 입니다.";
	 }	
}

public class TestMain {
	public static void main(String[] args) {
		A a  = new A();
		System.out.println(a);
		
	   }		
}
============================
출력 : 이것은 A 클래스 입니다.
```

답 : 다른 클래스로부터 상속 받지 않은 A class의 코드를 컴파일 하면 컴파일러는 위의 코드를 자동적으로 'extends Object'를 추가하여 A class가  Object 클래스로부터 상속 받도록 하기 때문에 Object클래스에 정의된 멤버들을 사용할 수 있다. 그래서 문자열을 리턴 하는 toString 메소드를 사용하였고 새로운 객체를 생성하여 리턴 하는 값을 출력하였다.

---

### 3. class 이름 및 함수 에서 final 의 의미는?

> 클래스와 메소드의 final 선언

- 클래스 앞에 final은 다른 클래스가 상속할 수 없다.
- 메소드 앞에 final은 다른 메소드가 오버라이딩을 할 수 없다.

---

### 4. 연습 문제 7-22 번을 푸시오.(보류)

- 7-22번 문제

    ```java
    문) 아래는 도형을 정의한 Shape클래스이다. 이 클래스를 조상으로 하는 Circle클래스와 
        Rectangle클래스를 작성하시오. 이 때, 생성자도 각 클래스에 맞게 적절히 추가해야 한다.

    (1) 클래스명 : Circle
    조상클래스 : Shape
    멤버변수 : double r - 반지름

    (2) 클래스명 : Rectangle
    조상클래스 : Shape
    멤버변수 : double width - 폭
    double height - 높이

    메서드 :
    1. 메서드명 : isSquare
    기 능 : 정사각형인지 아닌지를 알려준다.
    반환타입 : boolean
    매개변수 : 없음
    ====================================================================================
    abstract class Shape {
    	Point p;
    	Shape() {
    		this(new Point(0,0));
    	}
    	Shape(Point p) {
    		this.p = p;
    	}
    	abstract double calcArea(); // 도형의 면적을 계산해서 반환하는 메서드
    		Point getPosition() {
    			return p;
    	}
    	void setPosition(Point p) {
    		this.p = p;
    		}
    }
    class Point {
    	int x;
    	int y;
    	Point() {
    		this(0,0);
    	}
    	Point(int x, int y) {
    		this.x=x;
    		this.y=y;
    	}
    	public String toString() {
    		return "["+x+","+y+"]";
    		}
    }
    ```

- 7-22번 답

---

### 5. 연습 문제 7-23 번을 푸시오.(보류)

- 7-23번 문제

    ```java
    class Exercise7_23
    {
    /*
    (1) sumArea메서드를 작성하시오.
    */
    public static void main(String[] args){
    		Shape[] arr = {new Circle(5.0), new Rectangle(3,4), new Circle(1)};
    		System.out.println("면적의 합:"+sumArea(arr));
    	}
    }
    =======================================================================
    출력 : 면적의 합:93.68140899333463
    ```

- 7-23번 답

---

### 6. interface 와 class 의 차이는?

class는 상수와 함수를 선언하고 구현 할 수 있다. 하지만 interface는 상수와 함수를 선언만 하며 구현 부분이 없다. 그리고 class는 객체 생성과 선언이 가능, interface는 생성은 불가능 하고 선언만 가능하다.

---

### 7. 다음을 프로그램 하시오.[필수]

- 문제

    ```java
    interface Printable { // MS가 정의하고 제공한 인터페이스
       public void print(String doc);
    }
     SPrinterDriver 와 LPrinterDriver를 만드시오.
    ================================================

    public static void main(String[] args) {
       String myDoc = "This is a report about...";
       
       // 삼성 프린터로 출력
       Printable prn = new SPrinterDriver();
       prn.print(myDoc);
       System.out.println();

       // LG 프린터로 출력
       prn = new LPrinterDriver();
       prn.print(myDoc);
    }
    ================================================
    출력: From Samsung printer
    This is a report about ...

    From LG printer
    This is a report about ...
    ================================================
    ```

- 답

    ```java
    interface Printable { 
      public void print(String doc);
    }

    class SPrinterDriver implements Printable{
    	public void print(String doc){
    		@Override
    		System.out.println("From Samsung printer");
    		System.out.println(doc);
    	}
    }

    class LPrinterDriver implements Printable{
    	public void print(String doc){
    		@Override
    		System.out.println("From LG printer");
    		System.out.println(doc);
    	}
    }
    ```

---

### 8. @Override 에 대하여 설명하시오.

> @Override

- 상위 클래스의 메소드를 오버라이딩 하는 것이 목적이라는 선언.
- 오버라이딩 하는 형태가 아니면 컴파일러가 오류 메시지 전달.
- 부모 클래스에 있는 메소드를 자식클래스에서 재정의한 오버라이딩 메소드를 나타내는 키워드이다.

---

### 9.interface 에 대하여 설명하시오.

> interface

- 일종의 추상 클래스이다. 즉, 구현된 것은 아무 것도 없고 밑그림만 그려져 있는 '기본설계도'라 할 수 있다.
- 완성되지 않은 불완전한 것이기 때문에 그 자체만으로 사용 되기 보다 다른 클래스를 작성하는데 도움 줄 목적으로 작성된다.
- 인터페이스 사용법

```java
interface 인터페이스 이름{
	public static final 타입 상수이름 = 값;
	public abstract 메서드이름(매개변수 목록);
}
```

---

### 10.interface에 올 수 있는 두 가지는?

- 모든 멤버 변수는 public static final 이어야하며, 이를 생략할 수 있다.
- 모든 메소드는 public abstract이어야하며, 이를 생략할 수 있다.

---

### 11.abstract 키워드에 대하여 설명하시오.

> abstract

- 메소드의 선언부만 작성하고 실제 수행 내용은 구현하지 않은 추상 메서드를 선언하는데 사용된다.
- 다른 클래스가 abstract클래스를 상속 받아서 일부의 원하는 메소드만 오버라이딩 해도 된다는 장점이 있다.
- abstract에 사용될 수 있는 곳 - 클래스와 메서드 2가지이다.

---

### 12. 아래의 출력 결과가 아래와 같이 나오도록 프로그래밍 하시오.

- 문제

    ```java
    Object obj = new Circle(10);
    System.out.println(obj);
    ============================
    출력: 넓이는 100 입니다.
    ```

- 답

    ```java
    class Circle {
    	double r;
    	
    	Circle(double r){
    		this.r = r;
    	}
    	
    	public double getResult() {
    		return r * r * Math.PI;
    	}
    	
    	@Override
    	public String toString() {
    		return "넓이는 " + getResult() + " 입니다.";
    	}
    }
    ```

---

### 13. 아래의 메모리를 그리시오.

- 문제

    ```java
    class MobilePhone {
        protected String number;
        
        public MobilePhone(String num) {
            number = num;
        }    
        public void answer() {
            System.out.println("Hi~ from " + number);
        }
    }

    class SmartPhone extends MobilePhone { 
        private String androidVer;
        
        public SmartPhone(String num, String ver) {
            super(num);
            androidVer = ver;
        }    
        public void playApp() {
            System.out.println("App is running in " + androidVer);
        }
    }
    =======================================
    	MobilePhone phone = new SmartPhone("010-555-777", "Nougat");
        	phone.answer();    	
        	SmartPhone s = (SmartPhone)phone;    	
        	s.playApp();
    ```

- 답

    ![클래스](https://user-images.githubusercontent.com/75012998/102071228-86c94380-3e43-11eb-998f-c7e72cd411d1.jpg)


