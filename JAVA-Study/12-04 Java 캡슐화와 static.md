# 20-12-04(캡슐화와 static)
### 1. 아래의 접근제한자에 대하여 설명하시오.

```java
- public
- protected
- default
- private
```

> public

- 변수나 메소드는 외부 어디에서나 접근가능하고 다른패키지에서도 가능하다.

> protected

- 이 클래스를 상속하는 자식클래스에서 접근가능하고 같은 패키지 내에 클래스도 가능하다.

> default

- 동일한 패키지에 묶인 클래스내에서만 접근가능하다.

> private

- 해당 패키지 클래스내에서만 접근가능하다.

---

### 2. 지역변수에 접근제한자를 붙이지 않는 이유는?

- 지역변수라는 개념자체가 한 메소드, 반복문 또는 특정모듈안에서 사용되고 사라지는 것이기 때문에 접근제한자를 굳이 만들 필요가 없다.

---

### 3. 캡슐화에 대하여 설명하시오.

> Encapsulation

- 변수와 클래스를 하나로 묶는 작업이다.

**특징**

1. 중요한 데이터를 보존,보호를 위해 사용된다.
2. 외부에서 쉽게 접근하지 못하도록 정보은닉하는 작업이다.

**방법**

1. 맴버변수 앞에 접근제어자 private를 붙인다.
2. 맴버변수에 값을 넣고 꺼내올 수 있는 메소드를 만든다.(getter/setter메소드 활용)

---

### 4. 랜덤 숫자 맞추기 게임을 짜시오.

- Class 소스코드

    ```java
    import java.util.Random;
    import java.util.Scanner;

    public class RandomGame {
    	 Scanner sc = new Scanner(System.in);
    	 Random ran = new Random();
    	 
    	 public void print() {
    System.out.println("랜덤숫자 맞추기 게임을 시작하겠습니다.");
    		 
    		 while(true) {
    			 int count = 10;
    			 int com = ran.nextInt(100) + 1;
    			 while(count <= 10) {
    				 System.out.print("숫자를 선택해주세요 >> ");
    				 int user = sc.nextInt();
    				 
    				 if(user == com) {
    					 System.out.println("축하합니다" + count +"회 만에 정답입니다!");
    					 System.out.println("정답번호 : " + com);
    					 break;
    				 }else if(user < com) {
    					 count--;
    					 System.out.println("UP입니다.");
    					 System.out.println("남은 기회 : " + count);
    				 }else if (com < user) {
    					 count--;
    					 System.out.println("Down입니다.");
    					 System.out.println("남은 기회 : " + count);
    				 }
    			 }
    			 System.out.println("계속하시겠습니까? [Y/N]");
    			 String yn = sc.next();
    			 if(yn.equals("y") || yn.equals("Y")) {
    				 continue;
    			 }else {
    				 break;
    			 }
    		 }
    		System.out.println("프로그램을 종료하겠습니다.");
    		sc.close();
    	 }
    }
    ```

- Main 소스코드

    ```java
    public class TestMain {
    	
    	public static void main(String[] args) {
    		 RandomGame rg = new RandomGame();
    		 rg.print();
    	}	
    }
    ```

---

### 5. static 변수의 다른 용어 3가지를 말해 보시오.

1. 클래스 변수
2. 공유 변수
3. 정적 변수

---

### 6. 자바의 메모리 영역을 3가지로 나누고, 해당 영역에 들어가는 정보를 말하여 보시오.

> Method Area

- JVM에서 읽은 클래스와 인터페이스의 정보가 저장되는 영역
- 클래스 생성자와 메소드의 코드(바이트코드)가 저장된다.
- 클래스의 인스턴스가 생성된 후, 메소드가 실행되는 순간 클래스 정보가 Method Area 저장된다.

<img width="500" alt="MA" src="https://user-images.githubusercontent.com/75012998/103435645-ea7daa00-4c54-11eb-96b5-4841aed5997a.png">

> Call Stack

- 메소드 작업에 필요한 메모리 공간을 제공한다.
- 이 메모리에 메소드가 작업을 수행하는 동안 지역변수들과 연산의 중간결과를 저장한다.
- 메소드의 작업이 끝나면 할당된 메모리 공간은 반환되어 비어진다.

![stack](https://user-images.githubusercontent.com/75012998/103435654-fec1a700-4c54-11eb-8089-faedf0a1138b.jpg)

> Heap

- new 연산자 등으로 생성된 객체와 배열을 저장하는 영역
- Heap영역에 저장된 객체나 배열은 다른 객체에 참조될 수 있다.

<img width="500" alt="heep" src="https://user-images.githubusercontent.com/75012998/103435650-f6696c00-4c54-11eb-9f53-ce4854e2243b.png">

---

### 7. static 변수의 접근 방법은?

 **1. 내부 접근**

- static변수가 선언된 클래스내에서는 직접 이름만으로 접근가능

 **2. 외부 접근**

- private로 선언되지 않으면 클래스 외부에서 접근가능, 접근수준 지시자가 허용하는 범위에서 접근가능, 클래스 또는 인스턴스이름을 통해 접근가능

---

### 8. 클래스 변수의 활용의 예를 드시오.

```java
class Circle{
	// 한 클래스에 PI가 공통적으로 값을 가지기 위해 static선언하고 값이 변하지않게 상수로 고정
	static final double PI = 3.1415; 
	private double radius;

	Circle(double rad){
		radius = rad;
	}
	
	void showPerimeter(){
		double peri = (radius * 2) * PI;
	}
	
	void showArea(){
		double area = (radius * radius) * PI;
		System.out.println("넓이 : " + area); 
	}
}
```

---

### 9. 스태틱 함수에 인스턴스 변수가 올 수 없는 이유는?

Static 메소드는 인스턴스 생성없이 호출가능한 반면, 인스턴스 변수는 인스턴스를 생성해야지 존재하기 때문에 static이 붙은 메소드를 호출할 때 인스턴스가 생성 되었을수도 아닐수도  있기 때문에 static이 붙은 메소드에 인스턴스 변수가 올 수 없다.

---

### 10. 아래의 프로그램을 작성 하시오.

```java
다음 멤버를 가지고 직사각형을 표현하는 Rectangle 클래스를 작성하라.

- int 타입의 x, y, width, height 필드: 사각형을 구성하는 점과 크기 정보
- x, y, width, height 값을 매개변수로 받아 필드를 초기화하는 생성자
- int square() : 사각형 넓이 리턴
- void show() : 사각형의 좌표와 넓이를 화면에 출력
- boolean contatins(Rectangle r) : 매개변수로 받은 r이 현 사각형 안에 있으면 true 리턴
- main() 메소드의 코드와 실행 결과는 다음과 같다
public static void main(String[] args) {
   Rectangle r = new Rectangle(2, 2, 8, 7);
   Rectangle s = new Rectangle(5, 5, 6, 6);
   Rectangle t = new Rectangle(1, 1, 10, 10);
   
   r.show();
   System.out.println("s의 면적은 "+s.square());
   if(t.contains(r)) System.out.println("t는 r을 포함합니다.");
   if(t.contains(s)) System.out.println("t는 s를 포함합니다.");
}
==================================================================================================
(2,2)에서 크기가 8x7인 사각형
s의 면적은 36
t는 r을 포함합니다.
```

- Class 소스코드

    ```java
    public class Rectangle {
    	 private int x,y,width,height;
    	
    	Rectangle(int x , int y , int width, int height){
    		this.x = x;
    		this.y = y;
    		this.width = width;
    		this.height = height;
    	}
    	
    	public int square() {
    		return width * height;
    	}
    	
    	public void show() {
    		System.out.println("(" + x +"," + y + ")에서 크기가 " + width + "x" + height + "인 사각형");
    	}
    	
    	public boolean contains(Rectangle r) {
    		return true;
    	}
    }
    ```

- Main 소스코드

    ```java
    public class TestMain {
    	
    	public static void main(String[] args) {
    		 Rectangle r = new Rectangle(2, 2, 8, 7);
    		 Rectangle s = new Rectangle(5, 5, 6, 6);
    		 Rectangle t = new Rectangle(1, 1, 10, 10);
    		   
    		 r.show();
    		 System.out.println("s의 면적은 "+s.square());
    		 if(t.contains(r)) System.out.println("t는 r을 포함합니다.");
    		 if(t.contains(s)) System.out.println("t는 s를 포함합니다.");
    	}	
    }
    ```
