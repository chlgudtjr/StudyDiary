# 20-12-07 (JAVA 오버로딩,String객체)

### 1. 인스턴스 함수안에 스태틱 변수와 함수가 올수 있는 이유는?

- static변수는 선언 즉시 MA(Method Area)로 할당 되어진다.
- 인스턴스 함수는 객체를 생성한 다음에 MA(Method Area)로 할당 되어진다.

**결과** : static변수는 인스턴스 함수 안에 들어 갈수 있다.

---

### 2. 메소드 오버로딩이란?

- 같은 이름을 갖고 있지만, 서로 다른 매개변수 형식을 가지고 있는 메소드를 여러 개 정의하는 것.

**규칙**

1. 메소드명이 클래스명과 같아야 한다.
2. 매개변수의 타입과 갯수가 같아야 한다.

**예시**

```jsx
class OverLoadingEx{
	void overloadingex(){
	}
	void overloadingex(int i){
	}
	void overloadingex(int j, int k){
	}
}
```

---

### 3. 메소드 오버로딩을 적용한 대표적인 함수는?

> println()

- printstream 클래스에 소속되어있는 함수이다.
- 어떤 종류의 매개변수를 지정해도 출력할 수 있도록 한다.

**예시**

```java
public void println(String ex) {...}
public void println(double ex) {...}
public void println(float ex) {...}
public void println(long ex) {...}
public void println(int ex) {...}
public void println(char ex) {...}
public void println(boolean ex) {...}
```

---

### 4. this 함수에 대하여 설명하시오.

> this()

- 자기 자신의 생성자를 호출함으로서 생성자의 초기화 과정을 반복하지 않아도 된다.

    **예시**

```java
Class ThisMethodEx{
	private int myPhoneNum;
	private int uPhoneNum;

	ThisEx(int mpnum, int upnum) { // 생성자 함수
		myPhoneNum = mpnum;
		uPhoneNum = upnum;
	}

  ThisEx(int mpnum) {
		this(mpnum, 0); // this함수 쓴 경우
	}

	ThisEx(int upnum) {
		this(mpnum, upnum); // this함수 쓴 경우
	}
}
```

---

### 5. this란 무엇인가?

> this.

- 주로 생성자와 메소드의 매개변수 이름이 필드와 동일한 경우, 인스턴스 멤버인 필드임을 명시하고자 할때 사용됩니다.

 **예시**

```java
class ThisEx{
	private String name;
	private int age;
	
	ThisEx(String name, int age){
		this.name = name;
		this.age = age;
	}
}
```

---

### 6. 스트링 객체를 생성하는 2가지 방법은?

 **1. 일반적인 String 객체 생성 방법**

→ String str = new String("I am programmer");

 **2. " "을 사용하여 직접 대입하는 방법**

→ String str1 = "I am programmer";

---

### 7. 아래의 결과를 예측하고,이유를 설명하시오.

```java
String str1 = "Simple String";
String str2 = "Simple String";
   
String str3 = new String("Simple String");
String str4 = new String("Simple String");
   
if(str1 == str2)
	System.out.println("str1과 str2는 동일 인스턴스 참조");
else
	System.out.println("str1과 str2는 다른 인스턴스 참조");
   
if(str3 == str4)
	System.out.println("str3과 str4는 동일 인스턴스 참조");
else
	System.out.println("str3과 str4는 다른 인스턴스 참조");
```

**결과**

첫번째 → str1과 str2는 동일 인스턴스 참조
두번째 → str3과 str4는 다른 인스턴스 참조

**이유**

→ str1과 str2는 값을 직접 대입하여 객체를 생성하였지만 동일한 값을 참조하기 때문에 true값이 출력

![1](https://user-images.githubusercontent.com/75012998/104117356-0fb09d80-5364-11eb-9ade-e0387dcfb0d8.png)

→ str3와 str4는 new키워드를 사용하여 각각의 메모리공간을 할당하는 객체를 생성한다, 그래서 str3와 str4는 서로 다른 객체이고 다른 인스턴스를 참조하기 때문에 false 출력

![2](https://user-images.githubusercontent.com/75012998/104117358-13442480-5364-11eb-9a7c-30f3ed350530.png)

---

### 8. immutable 에 대하여 설명하시오.

> immutable

- 메모리에 재할당은 가능하지만, 한번 할당하면 내부 데이터를 변경할 수 없는 것.

**특징**

1. 객체에 대한 신뢰도가 높아집니다. 객체가 한번 생성되어서 그게 변하지 않는다면 transaction 내에서 그 객체가 변하지 않기에 우리가 믿고 쓸 수 있기 때문입니다.
2. 객체가 가지는 값마다 새로운 객체가 필요합니다. 따라서 메모리 누수와 새로운 객체를 계속 생성해야하기 때문에 성능저하를 발생시킬 수 있습니다.

**예시**

```java
class Immut{
	private final String name;
	
	public Immut(String name){
		this.name = name;
	}
}
```

---

### 9. 사용자로부터 받은 문자열(영문으로)에서 자음과 모음 개수를 계산하는 프로그램을 작성하라.

- Java 소스코드

    ```java
    import java.util.Scanner;

    class EnterWord{
    	public static void main(String[] args){
    		Scanner sc = new Scanner(System.in);
    		System.out.print("문자(영문)을 입력해주세요 >> ");
    		String word = sc.next(); // 문장을 입력할 변수
    		
    		int cons = 0; // 자음을 담을 변수
    		int coll = 0; // 모음을 담을 변수

    		for(int i = 0 ; i < word.length() ; i++){
    			switch(word.charAt(i)){ // 입력한 문장을  char형으로 비교
    /* 입력한 문장에 a,e,i,o,u 문자가 담겨져있을때 자음 갯수로 추가하고 
    		a,e,i,o,u 나올때까지 반복 후 없으면 switch문 빠져나옴
    */
    			case 'a' : 
    			coll++;
    			break;
    			case 'e' :
    			coll++;
    			break;
    			case 'i' :
    			coll++;
    			break;
    			case 'o' :
    			coll++;
    			break;
    			case 'u' :
    			coll++;
    			break;
    			default : // 모음이 아닌 자음문자들의 갯수를 추가함
    			cons++
    			}
    		}
    		System.out.println("자음의 갯수 : " + cons);
    		System.out.println("모음의 갯수 : " + coll);
    		System.out.println("프로그램을 종료하겠습니다.");
    		sc.close();
    	}
    }
    ```

---

### 10. 사용자로부터 키를 입력받아서 표준 체중을 계산한 후에 사용자의 체중과 비교하여 저체중인지, 표준인지, 과체중인지를 판단하는 프로그램을 작성하라. 표준 체중 계산식은 다음을 사용하라.

- Java 소스코드

    ```java
    import java.util.Scanner;

    class MyWeight{
    	public static void main(String[] args){
    		Scanner sc = new Scanner(System.in);
    		System.out.println("체중측정 프로그램을 시작하겠습니다.");
    		System.out.println("당신의 키를 입력하세요 >> ");
    		int height = sc.nextInt();
    		System.out.println("당신의 몸무게를 입력하세요 >> ");
    		int weight = sc.nextInt();
    	
    		double stkg = (height - 100) * 0.9; // 표준체중 구하는 공식
    		System.out.println("입력된 키의 표준체중입니다. >> " + stkg);

    		if(weight > stkg){ // 내 몸무게가 표준 체중 이상일 경우
    			System.out.println("당신은 과체중입니다.");
    		}else if(weight < stkg){ // 내 몸무게가 표준 체중 이하일 경우
    			System.out.println("당신은 저체중입니다.");
    		}else{ // 내 몸무게가 표준 체중일 경우
    			System.out.println("당신은 표준체중입니다.");
    		}
    		System.out.println("프로그램을 종료하겠습니다.");
    		sc.close();
    	}
    }
    ```

---

### 11. 2와 100 사이에 있는 모든 소수(prime number)를 찾는 프로그램을 작성하라. 주어진 정수 k를 2부터 k-1까지의 숫자로 나누어서 나머지가 0인 것이 하나라도 있으면 소수가 아니다.

- Java 소스코드

    ```java
    class PrimeNum{
    	public static void main(String[] args){
    		int k = 0;

    		for(int i = 2 ; i <= 100 ; i++){
    			int prime = 0;
    			for(int j = 0 ; j <= i - 1 ; j++){
    				if(i % j == 0){
    					prime++;
    				}
    			}
    			if(prime == 0){
    				System.out.println("소수 : " + i);
    				k++;
    			}
    		}
    		System.out.println("총 갯수 : " + k);
    	}
    }
    ```

---

### 12. 사용자에게 받은 문자열을 역순으로 화면에 출력하는 프로그램을 작성하시오.

- Java 소스코드

    ```java
    import java.util.Scanner;

    class ReverseWord{
    	public static void main(){
    		Scanner sc = new Scanner(System.in);
    		System.out.println("ReverseWord 프로그램을 시작하겠습니다.");
    		System.out.print("문자를 입력해주세요 >> ");
    		String word = sc.next();
    		
    		for(int i = word.length() ; i >= 0 ; i--){
    			System.out.print(word.charAt(i));
    		}
    		System.out.println(" ");
    		System.out.println("프로그램을 종료하겠습니다.");
    		sc.close();
    	}
    }
    ```
