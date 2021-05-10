# 20-11-24(JAVA 변수와 자료형)

### 1. 주석이란 무엇이며, 종류는?

- 프로그램 컴파일시 자동으로 코드가 비활성화 되어 실행에 문제가 없으며 주로 개발자들이 의견을 적거나 설명을 할 때 사용이 된다.

**종류**

1.  // : 한 줄 코드를 비활성화 한다.
2. /*  ~  */ : 여러 줄 코드를 비활성화 한다.

**주석의 예**

```java
class Comment{
	public static void main(String[] args){
		// 한 줄 주석

		/*
		여러 줄
		주석
		입니다.
		*/
	}
}
```

---

### 2. 들여쓰기는 왜 해야 되는가?

1. 방대한 여러 줄의 코드 가독성이 좋아 읽기 쉬워진다.
2. 클래스,메소드 { }안에 내용이 포함 되어졌다는 의미로도 사용된다.

**들여쓰기의 나쁜 예**

```java
class Bad{
public static void main(String[] args){
String str = "BadEx";
System.out.println(str);
}
}
```

**들여쓰기의 좋은 예**

```java
class Good{
	public static void main(String[] args){
		String str = "GoodEx";
		System.out.println(str);
	}
}
```

---

### 3. 변수란 무엇인가?

- 하나의 데이터를 저장 할 수있는 메모리 공간(메모리 주소는 OS가 결정)

**선언법**

1. 자료형타입 변수명; → 초기화 진행하지않고 선언만 한 변수
2. 자료형타입 변수명 = 값; → 선언과 초기화를 같이 한 변수

**규칙**

1. 변수명에 예약어와 숫자을 쓸 수 없다.
2. 대소문자를 구분하고 길이에 제한이 없다.
3. 둘 이상의 단어가 오면 카멜표기법을 사용한다. ex) helloWorld

---

### 4. 변수 선언의 의미는 무엇인가?

- 해당 자료형 메모리 크기만큼 메모리 공간 할당.

**변수의 예**

```java
class Variable{
	public static void main(String[] args){
		int variable; // 변수 선언의 예
	}
}
```

---

### 5. int num; 을 메모리로 설명해 보세요.

- 정수형 int타입이며 4byte 크기의 메모리에 num이름으로 할당 되는 변수를 선언한다.

![이](https://user-images.githubusercontent.com/75012998/104017827-2a680280-51fc-11eb-8b5e-75f0309dc238.png)

---

### 6. 8형제(자료형)을 써보세요(feat.외우세요).

![자료형](https://user-images.githubusercontent.com/75012998/101978539-049d1b80-3c99-11eb-940b-5c98b7f22203.jpg)

---

### 7. 문자가 뿌려지는 원리에 대하여 설명하시오.

- char ch = 'A';라는 변수가 있다면,
1. 일단 문자형 char타입에 대입되는 값을 아스키코드 표에서 번호를 찾고 그 번호를 2진수로 바꿔 컴퓨터가 이해하게 함. **(문자를 숫자로 바꾸는 인코딩 과정)**
2. 문자로 출력하기 위해 인코딩 과정에서 찾은 번호를 다시 아스키코드 표에서 문자를 찾아 출력하도록 한다. **(숫자를 문자로 바꾸는 디코딩 과정)**

---

### 8. 아스키 코드란 무엇인가요?

- 숫자를 이용하여 문자로 표현하기위한 127가지의 약속코드

**아스키코드 표**

![ascii](https://user-images.githubusercontent.com/75012998/101978543-0c5cc000-3c99-11eb-96be-db9ff33643ea.jpg)
