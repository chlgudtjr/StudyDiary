# 20-12-16(throws,equals함수)

### 1. throws 에 대하여 설명하시오.

> throws

1. 메소드에서 예외가 발생했을 때 예외를 호출한 쪽에서 처리하도록 던짐.
2. 현재 메소드에서 상위 메소드로 예외를 던진다.
- 선언법

```java
public void ex1() throws 예외처리 종류명{ //함수 앞에 위치함.
	...
} 

- 둘 이상 예외선언 시
public void ex2() throws 예외처리 종류1 , 종류2{
	...
} 
```

- 예시

![TR](https://user-images.githubusercontent.com/75012998/102431043-5279a100-4056-11eb-8d58-bdc972cf6906.jpg)

---

### 2. 아래가 컴파일 에러가 나는 이유에 대하여 설명하시오.

```java
try {
      int num = 6 / 0; 	
		} catch (Exception e) {
			e.printStackTrace();
		} catch (InputMismatchException e) {
			e.printStackTrace();
		}
```

- InputMismatchException 위 첫 번째 catch문에 Exception이라는 예외 처리 클래스중에 최고 조상클래스이며 다형성을 가지고 있는 키워드이므로 아래 InputMismatchException 내용을 담고 있어 첫 번째 cat문에서 예외 처리가 종료되므로 굳이 두 번째 catch문까지 갈 필요가 없기 때문에 컴파일러가 미리 친절하게 오류를 알려준다.

---

### 3. try with resource 에 대하여 설명하시오.

> try with resource

1. try(...)에서 선언된 객체들을 try가 종료될 때 자동으로 자원을 해제해주는 기능
2. try에서 선언된 객체가 AutoCloseable 인터페이스를 구현하였다면 Java는 try 구문이 종료될 때 객체의 close() 메소드를 호출해줌.
3. 코드를 짧고 간결하게 만들어 가독성이 높고 유지보수가 용이하다.
4. close()를 직접 적어줄 필요가 없기 때문에 실수로 빼먹어서 자잘한 버그가 발생할 확률이 낮아진다.

---

### 4. equals 함수에 대하여 설명하시오.

> equals

1. 매개변수로 객체의 참조변수를 받아 비교하고 그 결과 값을 boolean값으로 알려준다.
2. 오버라이딩을 통해 원하는 내용을 비교할 수 있도록 최상위 클래스인 object클래스에 정의.
- 예시

```java
public boolean equals(Object obj) {
     return (this == obj);
}
```

---

### 5. 과일, 사과, 배, 포도를 표현한 클래스를 만들고 이들 간의 관계를 고려하여 하나의 클래스를 추상 클래스로 만들어 메소드 print()를 구현하고 다음과 같은 소스와 결과가 나오도록 클래스를 작성하시오.

```java
Fruit fAry[] = {new Grape(), new Apple(), new Pear());

for(Fruit f : fAry)

f.print();

==========================================================
출력 : 나는 포도이다.
       나는 사과이다.
       나는 배이다.
```

답 : 

- Class 소스코드

    ```java
    abstract class Fruit {
    	
    	public abstract String print();
    }

    class Grape extends Fruit{
    	@Override
    	public String print() {
    		return "나는 포도이다";
    	}
    }

    class Apple extends Fruit{

    	@Override
    	public String print() {
    		return "나는 사과이다";
    	}
    	
    }

    class Pear extends Fruit{

    	@Override
    	public String print() {
    		return "나는 배이다";
    	}
    	
    }
    ```

- Main 소스코드

    ```java
    public class FruitMain {

    	public static void main(String[] args) {
    		
    		Fruit fAry[] = {new Grape(), new Apple(), new Pear()};
    		for(Fruit f1 : fAry)
    		System.out.println(f1.print());
    	}

    }
    ```

---

### 6. 다음 조건을 만족하도록 클래스 Person과 Student를 작성하시오.

```java
- 클래스 Person
* 필드 : 이름, 나이, 주소 선언
- 클래스 Student
* 필드 : 학교명, 학과, 학번, 8개 평균평점을 저장할 배열로 선언
* 생성자 : 학교명, 학과, 학번 지정
* 메소드 average() : 8개 학기 평균평점의 평균을 반환
- 클래스 Person과 Student 프로그램 테스트 프로그램의 결과
  : 8개 학기의 평균평점은 표준입력으로 받도록한다.
============================================================
출력:	이름 : 김다정
    	나이 : 20
	    주소 : 서울시 관악구
    	학교 : 동양서울대학교
	    학과 : 전산정보학과
	    학번 : 20132222
============================================================
8학기 학점을 순서대로 입력하세요
			
			1학기 학점  → 3.37
			2학기 학점  → 3.89
			3학기 학점  → 4.35
			4학기 학점  → 3.76
			5학기 학점  → 3.89
			6학기 학점  → 4.26
			7학기 학점  → 4.89
			8학기 학점  → 3.89
============================================================

8학기 총 평균 평점은 4.0375점입니다.
```

답 : 

- Class 소스코드

    ```java
    import java.util.Scanner;

    class Person1{
    	private String name;
    	private int age;
    	private String adress;
    	Scanner sc = new Scanner(System.in);
    	
    	Person1(){
    		this.name = name;
    		this.age = age;
    		this.adress= adress;
    	}
    	public void print() {
    		System.out.print("이름 : ");
    		String name = sc.next();
    		System.out.print("나이 : ");
    		String age = sc.next();
    		System.out.print("주소 : ");
    		String adress = sc.next();
    	}
    }

    class Student extends Person1{
    	private String sname;
    	private String depm;
    	private String id;
    	private double avg[] = new double [9];
    	
    	Scanner sc = new Scanner(System.in);
    	
    	Student(){
    		super();
    		this.sname = sname;
    		this.depm = depm;
    		this.id = id;
    	}
    	
    	public void getPrint() {
    		System.out.print("학교 : ");
    		sname = sc.next();
    		System.out.print("학과 : ");
    		depm = sc.next();
    		System.out.print("학번 : ");
    		id = sc.next();
    		System.out.println("======================");
    	}
    	
    	public void average() {
    		double count = 0;
    		int total = 0;
    		
    		for(int i=1 ; i <avg.length ; i++) {
    			System.out.print(i + "학기 학점 -> ");
    			count = sc.nextDouble() + avg[i];
    			total += count;
    		}
    		System.out.println("8학기 총 평균 평점은 " + (total/8.0) + "점 입니다.");
    		System.out.println("======================");
    	}
    	
    }
    ```

- Main 소스코드

    ```java
    class StudentMain{
    	public static void main(String[] args){
    		Student person = new Student();
    		person.print();
    		Student student = new Student();
    		student.getPrint();
    		Student student1 = new Student();
    		student1.average();
    	}
    }
    ```

---

### 7. 다음은 도형의 구성을 묘사하는 인터페이스이다. 다음 main() 메소드와 실행 결과를 참고하여, 인터페이스 Shape을 구현한 클래스 Circle를 작성하고 전체 프로그램을 완성하라.

```java
interface Shape {
   final double PI = 3.14; // 상수
   void draw(); // 도형을 그리는 추상 메소드
   double getArea(); // 도형의 면적을 리턴하는 추상 메소드
   default public void redraw() { // 디폴트 메소드
      System.out.print("--- 다시 그립니다.");
      draw();
   }
}
==========================================================
public static void main(String[] args) {
   Shape donut = new Circle(10); // 반지름이 10인 원 객체
   donut.redraw();
   System.out.println("면적은 "+ donut.getArea());
}
```

답 : 

- Class 소스코드

    ```java
    interface Shape {
    	   final double PI = 3.14; // 상수
    	   
    	   void draw(); // 도형을 그리는 추상 메소드
    	   
    	   double getArea(); // 도형의 면적을 리턴하는 추상 메소드
    	   
    	   default public void redraw() { // 디폴트 메소드
    		   
    	      System.out.print("--- 다시 그립니다.");
    	      draw();
    	   }
    	}

    class Cirle implements Shape {
    	int r;
    	
    	Cirle(int r){
    		this.r = r;
    	}
    	
    	@Override
    	public void draw() {
    		System.out.println(" 원 그리기");
    	}

    	@Override
    	public double getArea() {
    		return r * r * Math.PI;
    ```

- Main 소스코드

    ```java
    class CircleMain{
    	public static void main(String[] args) {
    		Shape donut = new Cirle(10); // 반지름이 10인 원 객체
    		donut.redraw();
    		System.out.println("면적은 "+ donut.getArea());
    	}
    }
    ```

---

### 8. 다음 main() 메소드와 실행 결과를 참고하여, 문제 7의 Shape 인터페이스를 구현한 클래스 Oval, Rect를 추가 작성하고 전체 프로그램을 완성하라.

```java
public static void main(String[] args) {
   Shape[] list = new Shape[3]; // Shape을 상속받은 클래스 객체의 레퍼런스 배열
   list[0] = new Circle(10); // 반지름이 10인 원 객체
   list[1] = new Oval(20, 30); // 20x30 사각형에 내접하는 타원
   list[2] = new Rect(10, 40); // 10x40 크기의 사각형
   for(int i=0; i<list.length; i++) list[i].redraw();
   for(int i=0; i<list.length; i++) System.out.println("면적은 "+ list[i].getArea());
}
--- 다시 그립니다.반지름이 10인 원입니다.
--- 다시 그립니다.20x30에 내접하는 타원입니다.
--- 다시 그립니다.10x40크기의 사각형 입니다.
면적은 314.0
면적은 1884.0000000000002
면적은 400.0
```

답 : 

- Class 소스코드

    ```java
    package InterfaceTest;

    interface Shape {
    	   final double PI = 3.14; // 상수
    	   
    	   void draw(); // 도형을 그리는 추상 메소드
    	   
    	   double getArea(); // 도형의 면적을 리턴하는 추상 메소드
    	   
    	   default public void redraw() { // 디폴트 메소드
    		   
    	      System.out.print("--- 다시 그립니다.");
    	      draw();
    	  }
    }

    class Cir implements Shape {
    	double r;
    	
    	public Cir(double r) {
    		this.r = r;
    	}
    	
    	public double getR() {
    		return r;
    	}

    	public void setR(int r) {
    		this.r = r;
    	}

    	@Override
    	public void draw() {
    		System.out.println("반지름이 " + r + "인 원입니다.");
    	} 
    	
    	@Override
    	public	double getArea() {
    		return r * r * PI;
    	}

    }

    class Oval extends Cir {
    	double r2;
    	
    	Oval(double r , double r2) {
    		super(r);
    		this.r2 = r2;
    	}
    	
    	@Override
    	public void draw() {
    		System.out.println(r + "x" + r2 + "에 내접하는 타원입니다.");
    	}
    	
    	@Override
    	public double getArea() {
    		return super.getR()* r2 * PI;
    	}
    }

    class Rect implements Shape {
    	private double weight, height;
    	
    	Rect(double weight, double height) {
    		this.weight = weight;
    		this.height = height;
    	}
    	
    	@Override
    	public void draw() {
    		System.out.println(weight + "x" + height + "크기의 사각형 입니다.");
    	}
    	
    	@Override
    	public double getArea() {
    		return weight * height;
    	}	

    }
    ```

- Main 소스코드

    ```java
    class ShapeMain{
    	public static void main(String[] args) {
    		Shape[] list = new Shape[3]; // Shape을 상속받은 클래스 객체의 레퍼런스 배열
    		list[0] = new Cir(10); // 반지름이 10인 원 객체
    		list[1] = new Oval(20, 30); // 20x30 사각형에 내접하는 타원
    		list[2] = new Rect(10, 40); // 10x40 크기의 사각형
    		for(int i=0; i<list.length; i++) list[i].redraw();
    		for(int i=0; i<list.length; i++) System.out.println("면적은 "+ list[i].getArea());
    	}
    }
    ```
