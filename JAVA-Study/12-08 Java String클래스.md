# 20-12-08(String클래스)

### 1. String 클래스에서 concat 메서드를 설명하시오.

> concat()

- 지정된 문자열을 연결할 문자열과 연결하며, 합친 문자열을 String으로 생성한다.
- 문자열을 추가할 때마다 new String()으로 생성되어 성능이나 속도가 좋지않다.

**선언법**

```java
class Ex{
	public static void main(String[] args){
		String str1 = "Hello";
		String str2 = "World";

		System.out.println("결과 : " + str1.concat(str2)); // 결과 : HelloWorld
										 // 지정할 문자열변수.concat(연결할 문자열);
	}
}
```

---

### 2. str.substring(2, 4); substring 사용법에 대하여 설명하시오.

> substring()

- 문자열 자르는 함수이다.

**선언법**

```java
// String.substring(start,end);

class Ex{
	public static void main(String[] args){
		String str1 = "Hello";
		System.out.println("결과 : " + str1.substring(2,4);); // 결과 : ll
	}
}
```

---

### 3. st1.compareTo(st2);compareTo 사용법에 대하여 설명하시오.

> compareTo()

- 두 문자열을 비교하고  int형 값으로 반환하는 메소드
- 두 문자열을 비교할 때 사전순으로 비교한다.

**선언법**

```java
// String.compareTo(비교할 문자열);

class Ex{
	public static void main(String[] args){
		String str1 = "aa";
	  String str2 = "aa";
    String str3 = "bb";
    String str3 = "cc";
    System.out.println(st1.compareTo(str2)); // str1과 str2의 값이 같기 때문에 0을 출력
    System.out.println(st1.compareTo(str3)); // str1과 str3의 값이 같지 않고 str3의 사전순 값이 낮기 때문에 -1을 출력
    System.out.println(st1.compareTo(str4)); // str1과 str4의 값이 같지 않고 str4의 사전순 값이 낮기 때문에 -2을 출력
	}
}
```

---

### 4. String.valueOf 에 대하여 설명하시오.

> valueOf()

- 기본 자료형의 지정한 값을 문자열로 반환해주는 역할을 한다.
- ()괄호 안에 해당 객체를 String 객체로 변환하는 역할

**선언법**

```java
// String.valueOf(변환할 객체);

class Ex{
	public static void main(String[] args){
		double db = 3.15864;
		System.out.println("결과 : " + String.valueOf(db)); // 결과 : 3.15864(문자열)
	}
}
```

---

### 5. 아래의 연산과정에서 호출되는 함수(원리)를 써서 표현해 보세요.

```java
String str = "age: " + 17;
```

- **답**

---

### 6. StringBuilder 와 String 의 차이는?

> StringBuilder

- String과 문자열을 더할 때 새로운 객체를 생성하지않고 기존의 데이터를 더하는 방식
- 속도가 빠르며 String과 비교해 상대적으로 메모리 부하가 적다.

**Ex)**

```java
class Ex{
	public static void main(String[] args){
		StringBuilder stb = new StringBuilder();
    stb.append("Hello"); // append는 문자열을 더하는 역할
    stb.append("World");
    System.out.println(stb.toString()); // toString은 생성한 객체를 String으로 변환하여 문자열로 출력이 가능하게 함.
	}
}
```

> String

- String은 불변의 객체이다.
- 두 String객체를 연산을 하면 새로운 객체를 생성하여 연산을 수행한다.
- StringBuilder에 비해 성능적으로 좋지않고 느려진다.

**Ex)**

```java
class Ex{
	public static void main(String[] args){
		String st1 = "Hello";
    String st1 = "World";
    String st1 = st1 + st2;
// 이렇게 하면 각각 4byte씩 메모리공간을 가지고있는 새로운 객체를 생성,
// 총 12byte 메모리용량을 가지고있는 객체가 되므로 성능으로 좋지않고 느려진다.
	}
}
```

---

### 7. String 을 이용하여 프로그래밍 하시오.

```java
입력 : 990925-1012999
출력 : 990925 1012999
```

- 정답 소스코드

---

### 8. 아래의 메모리 그림을 그리시오.

```java
int[] ar1 = new int[5];
```

![12](https://user-images.githubusercontent.com/75012998/104813487-d89f2800-584c-11eb-9518-04281f7bed5c.png)


---

### 9. 아래를 프로그래밍 하시오.(단 클래스로 구성할것)

```java
입력:lee sunkyo
출력:first name: lee second name:sunkyo
```

- Main 소스코드

    ```java
    class NameMain{
    	public static void main(String[] args){
    		Name name = new Name();
    		name.input();
    		name.print();
    	}
    }
    ```

- Class 소스코드

    ```java
    import java.util.Scanner;
    class Name{
    	private String fname,sname;
    	
    	Name(){
    		this.fname = fname;
    		this.sname = sname;
    	}
    	public void input() {
    		Scanner sc = new Scanner(System.in);
    		System.out.print("이름을 입력해주세요 : ");
    		fname = sc.next();
    		sname = sc.next();
    		sc.close();
    	}
    	
    	public void print() {
    		System.out.println("First name : " + fname + " Seconds name : " + sname);
    	}
    }
    ```

---

### 10. 아래를 프로그래밍 하시오.

```java
입력 : 홍 길동 
출력 : 성 = 홍  이름 = 길동 

입력 : 홍길동 
출력 : 공백이 없군요. 다시 입력해주세요.
```

- class 소스코드

    ```java
    package java_1208;

    import java.util.Scanner;
    public class KoreanName {
    	private String familyName; //local 변수 일때는 직접 초기화.
    	private String givenName;
    	private String input;
    	private int blank;
    	private int length;
    	
    	Scanner sc;
    	
    	public void askName() {
    		sc = new Scanner(System.in);
    		System.out.println("이름을 입력하세요 (예: 홍 길동)");
    	}
    	
    	public void inputName() {
    		input = sc.nextLine();
    	}
    	
    	public boolean checkBlank() {
    		if(input.contains(" "))
    			return true;
    		return false;
    	}
    	
    	private void whereIsBlank() {
    		for(int i=0; i<input.length(); i++) {
    			if(input.charAt(i) == ' ') {
    				blank = i;
    			}
    		}
    	}
    	
    	private void leghtOfName(){
    		length = input.length();
    	}
    	
    	private void splitName() {
    		familyName = input.substring(0, blank);
    		givenName = input.substring(blank+1, length);
    	}
    	
    	private void pirntName() {
    		System.out.println("성 = "+ familyName + ", 이름 = "+ givenName);
    	}
    	
    	public void doAgainPrint() {
    		System.out.println("공백이 없군요. 다시 입력해 주세요.");
    	}
    	
    	public void blankCheck_namePrint() {
    		whereIsBlank();
    		leghtOfName();
    		splitName();
    		pirntName();
    	}
    }
    ```

- Main 소스코드

    ```java
    import java.util.Scanner;

    public class KrNameMain {

    	public static void main(String[] args) {
    		
    		KoreanName whichName = new	KoreanName();
    		whichName.askName();
    	
    		while(true) {
    			whichName.inputName();
    			
    			if(whichName.checkBlank()) {
    				whichName.blankCheck_namePrint();
    				break;
    			}else {
    				whichName.doAgainPrint();
    				continue;
    			}
    		}
    	}
    }
    ```

---

### 11. 아래를 프로그래밍 하시오.

```java
입력: Hello.java
출력: 파일이름은:Hello 이며 확장자는 java 입니다.

입력: Java.avi 
출력: 파일이름은:Java 이며 확장자는 avi 입니다.
```

- class 소스코드

    ```java
    import java.util.Scanner;

    public class Saperate {
    	private String filename;

    	public void Saperate() {

    	}

    	public void Saperate(String filename) {
    		this.filename = filename;
    	}

    	public String getName() {
    		return filename;
    	}

    	public void setName(String filename) {
    		this.filename = filename;
    	}

    	public void input() {
    		Scanner sc = new Scanner(System.in);
    		System.out.println("이름을 입력하세요!");
    		filename = sc.nextLine();
    		sc.close();
    	}

    	public void Name() {// ab.java
    		for (int i = 1; i <= filename.length(); i++) {
    			if (filename.substring(i - 1, i).equals(".")) {
    				System.out.println("파일이름은: " + filename.substring(0, i - 1) + " 이며 확장자는 " + filename.substring(i) + "입니다.");
    			}
    		}
    	}
    }
    ```

- Main 소스코드

    ```java
    class SaperateMain{
    	public static void main(String[] args) {

    		Saperate a = new Saperate();
    		a.input();
    		a.Name();
    	}
    }
    ```

---

### 12. Scanner 클래스를 이용해서 한 줄 읽고, 공백으로 분리된 "단어"가 몇 개 들어 있는지 확인해보자.

```java
"그만"을 입력할 때까지 반복하는 프로그램이다.
힌트(split 함수를 이용해 볼것)

예) 입력 : Java Programming 
출력 : 단어의 개수는 2
입력 : 자바 수업은 2층 C클래스 
출력 : 단어의 개수는 4
입력 : 그만 > 출력 : 프로그램 종료
```

- class 소스코드

    ```java
    import java.util.Scanner;

    public class WordsCount {
    	private String words;

    	public WordsCount() {

    	}

    	public WordsCount(String words) {
    		this.words = words;
    	}

    	public void setWords(String words) {
    		this.words = words;
    	}

    	public String getWords() {
    		return words;
    	}

    	public void result() {

    		Scanner sc = new Scanner(System.in);
    		while (true) {
    			System.out.println("문장을 입력하세요!");
    			words = sc.nextLine();
    			String[] arr = words.split(" ");

    			if(words.equals("그만")) {
    				System.out.println("프로그램 종료");
    				break;
    			}else {
    				System.out.println("단어의 개수는 " + arr.length);
    				continue;
    			}
    		}
    		sc.close();
    	}
    }
    ```

- Main 소스코드

    ```java
    class WordsCount Main{
    	public static void main(String[] args) {
    		WordsCount a = new WordsCount();
    		a.result();
    	}
    }
    ```
