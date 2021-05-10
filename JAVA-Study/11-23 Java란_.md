# 11-23(Java 기초)

### 1. HelloWorld를 출력하는 프로그램의 과정을 설명하시오.(cmd창)

> 답 :

```java
class HelloWorld{
	public static void main(String[] args){
		System,out.println("Hello World!");
	}
}
```

1. cmd 실행 후 notepad HelloWorld.java를 입력한다.
2. 메모장이 켜지고  메모장에 위 소스코드를 입력 후 저장한다.
3. 다시 cmd창으로 와서 javac HelloWorld.java을 입력하여 컴파일해준다
4. 입력 후 아무 것도 뜨지 않았다면 컴파일이 된 것이다. 그리고 메모장으로 저장한 java파일 경로에서 .class 파일이 생성되었을 것이다.
5. java HelloWorld.java를 입력하면 Hello World가 출력 되어진 것을 알 수 있다.
- 그림 예시

![213](https://user-images.githubusercontent.com/75012998/101977421-b552ed00-3c90-11eb-8e4e-39c6066ecd27.jpg)
    

- .class파일 확인하기
    - cmd창에 HelloWorld.java을 저장한 경로와 함께 dir/w입력 후 아래 파일목록이 쭉 나올텐데 잘 찾아보면 HelloWorld.class파일로 저장되어 있을 것이다.

   
![12](https://user-images.githubusercontent.com/75012998/101977403-a66c3a80-3c90-11eb-9d67-2d7d655f63ae.jpg)

---

### 2. 아래의 명령어를 설명하시오(뭐하는건가).

> javac

답 : 자바코드를 작성한 소스파일(.java)을 자바 가상머신이 인식 할 수 있는 바이트 코드(.class) 타입   으로 변환시켜주는 명령어

> java

답 : java는 사용자가 규칙에 맞게 작성한 모든 소스코드 파일.

---

### 3. 컴파일이란 무엇인가요?

답 : 사용자가 고급언어로 만든 파일을 컴퓨터에 실행시키기 위해 기계어로 번역하는 명령어

---

### 4. java 언어를 창시한 사람은?

답 :  캐나다 출신의 소프트웨어 개발자 '제임스 고슬링'이다.

- 제임스 고슬링의 대한 자세한 문서는 아래 링크를 통해 알아 보자!

[제임스 고슬링 ](https://namu.wiki/w/%EC%A0%9C%EC%9E%84%EC%8A%A4%20%EA%B3%A0%EC%8A%AC%EB%A7%81)

---

### 5. JDK란 무엇이며, 어디서 다운로드 받으며, OS별로 버전이 있는 까닭은?

> JDK (Java Develoment Kit)

답 : Java 환경에서 돌아가는 프로그램을 개발하는 데 필요한 툴들을 모아놓은 소프트웨어 패키지.

- 다운로드 받는 곳

[Java SE Downloads](https://www.oracle.com/kr/java/technologies/javase-downloads.html)

- OS별로 버전이 있는 이유

: 각 운영체제별로 실행 될 수 있는 개발 환경이 다르기 때문이다.

---

### 6. JVM 무엇의 약자이며,이란 무엇인가?

> JVM (Java Virtual Machine)

답 : 자바와 os사이에서 중계자 역할,메모리를 관리해주고 os에 구애받지않고 재사용 가능

- 그림 예시

![jvm](https://user-images.githubusercontent.com/75012998/101977428-bc79fb00-3c90-11eb-9657-6d7d8990053b.jpg)
