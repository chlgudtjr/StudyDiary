
# 20-12-18(BigInteger클래스)

### 1. BigInteger 클래스에 대하여 설명하시오.

> BigInteger

- 자바 정수 범위 이상의 숫자를 정수를 표현할 때 쓰인다.

선언법

```java
BigInteger bigNumber = new BigInteger("초기화 값");
/* 매개 변수를 정수 표현 대신 문자열로 선언하는 이유는 숫자형으로 표현할 수 있는 값을 
	 벗어나기 때문에 문자열로 표시한다.
*/
```

계산법

```java
		BigInteger bigNumber = new BigInteger("10000");
		BigInteger bigNumber = new BigInteger("10000");

		//BigInteger 기반 덧셈 연산
		BigInteger r1 = big1.add(big2);
		System.out.println("덧셈결과 : " + r1);
		
		//BigInteger 기반 뺄셈 연산
		BigInteger r4 = big1.subtract(big2);
		System.out.println("뺄셈 결과 : " + r4);
		System.out.println();
		
		//BigInteger 기반 곱셈 연산
		BigInteger r2 = big1.multiply(big2);
		System.out.println("곱셈 결과 : " + r2);
		System.out.println();
		
		//BigInteger 기반 나눗셈 연산
		BigInteger r3 = big1.divide(big2);
		System.out.println("나눗셈 결과 : " + r3);
		System.out.println();

/*
BigInteger클래스는 사칙연산이 안된다. 왜냐하면 문자열로 초기화값을 가지기 때문이다.
그래서 사칙연산하기 위해서는 BigInteger클래스 내부 메소드를 이용하여 연산을 진행 해야한다.
*/
```

더 많은 정보를 알아보고 싶다면 아래 링크를 참조!!

[[Java] 큰 숫자(정수) 다루기 BigInteger 사용법 & 예제 총정리](https://coding-factory.tistory.com/604)

---

### 2. 아래의 결과 값은 false 출력이 된다. true가 되도록 INum을짜시오.

```java
INum[] ar1 = new INum[3];
INum[] ar2 = new INum[3];

ar1[0] = new INum(1);
ar2[0] = new INum(1);

ar1[1] = new INum(2);
ar2[1] = new INum(2);

ar1[2] = new INum(3);
ar2[2] = new INum(3);

System.out.println(Arrays.equals(ar1, ar2));
```

답 :

- Class 소스코드

    ```java
    class INum{
    	private int num;
    	
    	public INum(int num){
    		this.num = num;
    	}	
    	
    	public boolean equals(Object obj){
    		if(this.num == ((INum)obj).num){
    			return true;
    		}else{
    			return false;
    		}
    	}
    }
    ```

- Main 소스코드

    ```java
    class INumMain{
    	public static void main(String[] args) {
    		Inum[] ar1 = new Inum[3];
    		Inum[] ar2 = new Inum[3];
    		
    		ar1[0] = new Inum(1);
    		ar2[0] = new Inum(1);
    		
    		ar1[1] = new Inum(2);
    		ar2[1] = new Inum(2);
    		
    		ar1[2] = new Inum(3);
    		ar2[2] = new Inum(3);
    		
    		System.out.println(Arrays.equals(ar1, ar2));
    	}

    }
    ```

---

### 3. 아래에서 정렬이 이름 순으로 되게 하시오. (Person 객체를 만드시오.)

```java
class ArrayObjSearch {
    public static void main(String[] args) {
        Person[] ar = new Person[3];

        ar[0] = new Person("Lee", 29);
        ar[1] = new Person("Goo", 15);
        ar[2] = new Person("Soo", 37);

        Arrays.sort(ar);
```

답 : 

- Class 소스코드

    ```java
    class Person implements Comparable{
    	private String name;
    	private int age;
    	
    	Person(String name, int age){
    		this.name = name;
    		this.age = age;
    	}
    	
    	public String toString() {
    		return name + ":" + age;
    	}

    	@Override
    	public int compareTo(Object o) {
    		Person p = (Person)o;
    		return this.name.compareTo(((Person)o).name);
    	}
    }
    ```

- Main 소스코드

    ```java
    class PersonMain{
    public static void main(String[] args) {
    		Pers[] ar = new Pers[3];

        ar[0] = new Pers("Lee", 29);
        ar[1] = new Pers("Goo", 15);
        ar[2] = new Pers("Soo", 37);

        Arrays.sort(ar);
        for(Pers p : ar) {
    	    System.out.println(p);
         }
    	}
    }
    ```

---

### 4. 위의 문제에서 사람의 이름 글자 수가 많은 순으로 정렬을 되게끔 person 객체를 만드시오

답 : 

- Class 소스코드

    ```java
    class Person implements Comparable{
    	private String name;
    	private int age;
    	
    	Person(String name, int age){
    		this.name = name;
    		this.age = age;
    	}
    	
    	public String toString() {
    		return name + ":" + age;
    	}

    	@Override
    	public int compareTo(Object o) {
    		Person p = (Person)o;
    		return ((Person)o).name.length() - name.length();
    	}
    }
    ```

- Main 소스코드

    ```java
    class PersonMain{
    public static void main(String[] args) {
    		Pers[] ar = new Pers[3];

        ar[0] = new Pers("Lee", 29);
        ar[1] = new Pers("Goo", 15);
        ar[2] = new Pers("Soo", 37);

        Arrays.sort(ar);
        for(Pers p : ar) {
    	    System.out.println(p);
         }
    	}
    }
    ```

---

### 5. 경과시간을 맞추는 게임을 작성하라. 다음 예시를 참고하면, <Enter> 키를 입력하면 현재 초 시간을 보여주고 여기서 10초에 더 근접하도록 다음 <Enter> 키를 입력한 사람이 이기는 게임이다.

```java
10초에 가까운 사람이 이기는 게임입니다.
황기태 시작 키  >>
	현재 초 시간 = 42
10초 예상 후 키  >>
	현재 초 시간 = 50
이재문 시작 키  >>
	현재 초 시간 = 51
10초 예상 후 키  >>
	현재 초 시간 = 4
황기태의 결과 8, 이재문의 결과 13, 승자는 황기태
```

답 :

- Class 소스코드
- Main 소스코드

---

### 6. 제네릭이란??

> Generic

- 클래스 내부에서 사용할 데이터 타입을 외부에서 지정하는 기법을 의미한다.
- 객체의 타입을 컴파일 시점에 체크하기 때문에 타입 안정성을 높이고 형 변환의 번거로움을 줄일 수 있습니다.
- 제네릭 타입을 사용함으로써 잘못된 타입이 사용될 수 있는 문제를 컴파일 과정에서 제거할 수 있다.

제네릭 이전의 코드(잘못된 예)

```java
class GenericExMain{
	public static void main(String[] args){
		Box aBox = new Box(); // 상자 생성
		Box oBox = new Box(); // 상자 생성
		
		aBox.set("Apple"); // 상자에 사과를 담는다.
		oBox.set("Orange"); // 상자에 오렌지를 담는다.
							
		System.out.println(aBox.get());
		System.out.println(oBox.get());
// 프로그래머의 실수가 컴파일 과정, 실행과정에서 발견되지 않음.
	}
}
```

제네릭 이후의 코드(개선된 예)

```java
class Box<T>{
	private T ob;
	
	public void set(T o){
		ob = o;
	}
	public T get(){
		return ob;
	}
	public static void main(String[] args){
		Box<Apple> aBox = new Box<Apple>(); // T를 Apple로 결정
		Box<Orange> oBox = new Box<Orange>(); // T를 Orange로 결정	
	
		aBox.set(new Apple()); // 상자에 사과를 담는다.
		oBox.set(new Orange()); // 상자에 오렌지를 담는다.
							
		Apple ap = aBox.get(); // 사과를 꺼내는데 형 변환 하지 않는다.
		Orange og = oBox.get(); // 오렌지를 꺼내는데 형 변환 하지 않는다.

		System.out.println(ap);
		System.out.println(og);

		/* 만약 이렇게 출력문을 썻다면 컴파일 오류로 알려줘서 프로그래머의 실수를 알아차리게 한다.
		System.out.println(aBox.get());
		System.out.println(oBox.get());
		*/

	}
}
```

---

### 7. 아래를 프로그래밍 하시오.

```java
Rectangle r1 = new Rectangle(5,6);
Rectangle r2 = new Rectangle(7,9);

Rectangle r3 = Rectangle.compareRect(r1,r2);

System.out.println(r3.getHeight() + " : " + r3.getWidth()  + "입니다.");
=============================
출력 : 9 : 7 입니다.
```

답 : 

- Class 소스코드

    ```java
    class Rec {
    	private int n1,n2;
    	
    	Rec(int n1, int n2){
    		this.n1 = n1;
    		this.n2 = n2;
    	}

    	
    	private int getWidth() {
    		return n1;
    	}

    	private int getHeight() {
    		return n2;
    	}
    	
    	private static Rec compareRect(Rec r1, Rec r2) {
    		if(r1.n1 * r1.n2 > r2.n1 * r2.n2) {
    				return r1;
    			}else {
    				return r2;
    			}
    		}
    	}
    }
    ```

- Main 소스코드

    ```java
    class RecMain{
    	public static void main(String[] args){
    		Rectangle r1 = new Rectangle(5,6);
    		Rectangle r2 = new Rectangle(7,9);

    		Rectangle r3 = Rectangle.compareRect(r1,r2);

    		System.out.println(r3.getHeight() + " : " + r3.getWidth()  + "입니다.");
    	}
    }
    ```

---

### 8. 아래를 프로그래밍 하시오.

```java
- Rectangle 배열 4개를 만든후 스캐너 객체로 가로와 세로를 입력하여 4개의 객체를 배열에 할당한다. 
- getSortingRec 사각형 배열을 내림차순 정렬한다.
- 정렬이 제대로 되었는지 배열에 저장된 객체의 getArea()함수를 순서대로 호출한다.

Rectangle[] rec = new Rectangle[3];
........
Rectangle[] recSorting = Rectangle.getSortingRec(rec) 
......
```

답 :

- Class 소스코드
- Main 소스코드
