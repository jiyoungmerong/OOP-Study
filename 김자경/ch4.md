# 04 자바가 확장한 객체 지향

### 1️⃣ abstract 키워드
- 추상 클래스는 인스턴스, 즉 객체를 만들 수 없다 → `new`를 사용할 수 없다
- 추상 메서드는 하위 클래스에게 메서드의 구현을 강제한다 → 오버라이드 강제
- 추상 메서드를 포함하는 클래스는 반드시 추상 클래스여야 한다
```
  💡 참고
     * 추상 메서드(Abstract Method) : 선언부는 있는데 구현부가 없는 메서드
     * 추상 클래스 : 추상 메서드를 하나라도 가지고 있는 클래스
``` 

### 2️⃣ 생성자
```java
클래스 객체명 = new 클래스();
```
```java
동물 뽀로로 = new 동물();
```
- 클래스의 인스턴스 즉, 객체를 만들 때마다 `new` 키워드를 사용
- 객체 생성자 메서드(=생성자) : 반환값이 없고 클래스명과 같은 이름을 가진 메서드 → 객체를 생성하는 메서드

#### ⭐ 꼭 기억해야 할 자바 특징
- 개발자가 아무런 생성자도 만들지 않으면 자바는 인자가 없는 기본 생성자를 자동으로 만들어준다
- 인자가 있는 생성자를 하나라도 만든다면 자바는 기본생성자를 만들어 주지 않는다

생성자는 개발자가 필요한 만큼 오버로딩해서 만들 수 있다.

### 3️⃣ static 블록
클래스가 static 영역에 배치될 때 실행되는 코드 블록
```
  💡 참고
     객체 생성자는 존재하지만 클래스 생성자는 존재하지 않는다.
``` 
```java
public class Driver05 {
	public static void main(String[] args) {
		System.out.println("main 메서드 시작!");
		System.out.println(Animal.age);
	}
}

class Animal {
	static int age = 0;

	static {
		System.out.println("Animal class ready on!");
	}
}
```
위 코드에서 Animal의 static 블록은 Animal.age로 정적 속성을 사용할 때 처음 실행된다.
클래스 정보는 해당 클래스가 코드에서 맨 처음 사용될 때 T 메모리 static 영역에 로딩되며, 이 때 단 한 번만 해당 클래스의 static 블록이 실행된다.

#### 📌 클래스가 제일 처음 사용되는 3가지 경우
1. 클래스의 정적 속성을 사용할 때
2. 클래스의 정적 메서드를 사용할 때
3. 클래스의 인스턴스를 최초로 만들 때

### 4️⃣ final 키워드
#### 📌 final 키워드가 나타날 수 있는 곳
1. 클래스
2. 변수
3. 메서드

**⭐ final 클래스는 상속을 허락하지 않는다 → 하위 클래스를 만들 수 없다**

```java
public class 고양이 {
	final static int 정적상수1 = 1;
	final static int 정적상수2;

	final int 객체상수1 = 1;
	final int 객체상수2;

	static {
		정적상수2 = 2;

		// 상수는 한번 초기화 되면 값을 변경할 수 없다.
		// 정적상수2 = 4;
	}

	고양이() {
		객체상수2 = 2;

		// 상수는 한번 초기화 되면 값을 변경할 수 없다.
		// 객체상수2 = 4;

		final int 지역상수1 = 1;
		final int 지역상수2;

		지역상수2 = 2;
	}
}
```
#### 📌 final 변수 초기화 방법
- final static을 정의된 정적 상수는 선언과 동시에 초기화하거나 정적 생성자에 해당하는 static 블록 내부에서 초기화 가능
- final [type]으로 정의된 객체 상수는 똑같이 객체 상수 선언과 동시에 초기화 하거나 객체 생성자에서 초기화 가능
```java
public class 동물 {
	final void 숨쉬다() {
		System.out.println("호흡 중");
	}
}

class 포유류 extends 동물 {
	// 에러 발생: Cannot override the final method from 동물
	void 숨쉬다() { 
        System.out.println("호흡 중"); 
    }
}
```
메서드가 final이면 최종 메서드이므로 **오버라이딩을 금지**한다.

### 5️⃣ instanceof 연산자
만들어진 객체가 특정 클래스의 인스턴스인지 확인하는 연산자
```java
객체_참조_변수 instanceof 클래스명 // instanceof 연산자 사용법
```

 
```java
class 동물 {

}

class 조류 extends 동물 {

}

class 펭귄 extends 조류 {

}

public class Driver {
	public static void main(String[] args) {
		동물 동물객체 = new 동물();
		동물 조류객체 = new 조류();
		동물 펭귄객체 = new 펭귄();

		System.out.println(동물객체 instanceof 동물);

		System.out.println(조류객체 instanceof 동물);
		System.out.println(조류객체 instanceof 조류);

		System.out.println(펭귄객체 instanceof 동물);
		System.out.println(펭귄객체 instanceof 조류);
		System.out.println(펭귄객체 instanceof 펭귄);

		System.out.println(펭귄객체 instanceof Object);
	}
}
```
실행 결과는 **모두 true**가 출력된다.

펭귄객체 instanceof 동물 가 참인 이유는 **객체 참조 변수 타입**이 아닌 **실제 객체의 타입**에 의해 처리되기 때문이다.

객체 지향 설계 5원칙 가운데 LSP(리스코프 치환 법칙)을 어기는 코드에서 주로 나타나는 연산자이다. **→ 리팩토링의 대상**

### 6️⃣ package 키워드
네임스페이스(이름공간)을 만들어주는 역할

**📌 네임스페이스의 필요성**

여러 개발 조직이 하나의 프로젝트에 참가할 때 발생할 수 있는 변수명 중복 문제를 package를 통해 이름 공간을 나누어 해결한다.
ex) `package명.변수명`

### 7️⃣ interface 키워드와 implements 키워드
인터페이스는 public 추상 메서드와 public 정적 상수만 가질 수 있다.

따라서 메서드에 `public`, `abstract` 속성에 `public`, `static`, `final`을 붙이지 않아도 자바가 자동으로 붙여준다.

```java
interface Speakable {
	double PI = 3.14159;
	final double absoluteZeroPoint = -275.15;

	void sayYes();
}
```
```java
interface Speakable {
	public static final double PI = 3.14159;
	public static final double absoluteZeroPoint = -275.15;

	public abstract void sayYes();
}
```
위 두 코드는 동등한 코드이다.

#### 📌 람다(Lambda)
- 람다란 함수(=로직)를 의미하고 변수에 할당할 수 있다
 → 람다는 변수에 저장할 수 있는 로직이다
- 변수에 로직을 저장할 수 있고, 로직을 메서드의 인자로 쓸 수 있고, 로직을 메서드의 반환값으로 사용할 수 있다
- 자바에서 람다는 인터페이스를 기초로 하고 있어 **default 메서드**라고 하는 객체 구상 메서드와 정적 추상 메서드를 지원할 수 있다.

### 8️⃣ this 키워드
객체 멤버 메서드 내부에서 객체 자기 자신을 지칭할 때 쓰는 키워드
```java
class 펭귄 {
	int var = 10;

	void test() {
		int var = 20;

		System.out.println(var);
		System.out.println(this.var);
	}
}

public class Driver {
	public static void main(String[] args) {
		펭귄 뽀로로 = new 펭귄();
		뽀로로.test();
	}
}
``` 
![4](https://github.com/GDSC-SKHU/OOP-Study/assets/80957486/06b69fb4-050b-4ce2-91ea-77527474be37)

위 코드를 실행하게 되면

`System.out.println(var);` 는 `뽀로로.test()` 지역변수가 있는 스택프레임의 var를 출력하게되고

`System.out.println(this.var);` 펭귄 객체 변수는 지역변수와 이름이 중복되므로 `this.var`라고 지정해줘야 한다.

 
#### ⭐ 기억해야 될 것
- 지역 변수와 속성(객체 변수, 정적 변수)의 이름이 같은 경우 지역 변수가 우선한다.
- 객체 변수와 이름이 같은 지역 변수가 있는 경우 객체 변수를 사용하려면 `this`를 접두사로 사용한다.
- 정적 변수와 이름이 같은 지역 변수가 있는 경우 정적 변수를 사용하려면 클래스명을 접두사로 사용한다.

### 9️⃣ super 키워드
바로 위 상위 클래스의 인스턴스를 지칭한다.
```java
class 동물 {
	void method() {
		System.out.println("동물");
	}
}

class 조류 extends 동물 {
	void method() {
		super.method();
		System.out.println("조류");
	}
}

class 펭귄 extends 조류 {
	void method() {
		super.method();
		System.out.println("펭귄");

		// Syntax error on token "super", Identifier expected
		// super.super.method();
	}
}

public class Driver {
	public static void main(String[] args) {
		펭귄 뽀로로 = new 펭귄();
		뽀로로.method();
	}
}
```
위 코드처럼 `super` 키워드를 통해 상위 클래스의 인스턴스 메서드를 호출할 수 있다.

하지만, `super.super` 형태의 상위의 상위 클래스의 인스턴스에는 접근이 불가능하다.
