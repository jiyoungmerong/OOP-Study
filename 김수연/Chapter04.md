# 4장

## 목차
- 추상 메서드와 추상 클래스
- 생성자
- 클래스 생성 시의 실행 블록, static 블록
- final 키워드
- instanceof 연산자
- 패키지 [package]
- interface 키워드와 implements 키워드
- this 키워드
- super 키워드

# 1. abstract 키워드 - 추상 메서드와 추상 클래스
- 추상 메서드 : 선언부는 있는 데 구현부가 없는 메서드
 
  → 추상메서드를 하나라도 갖고 있는 클래스는 반드시 추상 클래스로 선언해야 한다.

    → 추상 클래스 내에 선언된 추상 메서드는 자식 클래스에서 구현될 수 있으며, 자식 클래스에서는 반드시 추상 메서드를 구현해야 한다.
    
- 추상 클래스 : 추상 클래스는 인스턴스, 즉 객체를 만들 수 없다.

# 2. 생성자

> 객체를 생성하는 메서드 (객체 생성자 메서드) = 생성자

```java
Animal lion = new Animal();
```
- new Animal() : 반환값이 없고 클래스 명과 같은 이름을 가진 메서드를 객체를 생성하는 메서드라고 해서 객체 생성자 메서드라 한다. 이를 줄여서 **생성자**라 부른다.

→ 클래스에 아무런 생성자 메서드가 없다면 컴파일 과정에서 자바 컴파일러가 알아서 기본 생성자를 만들어 줌.

```java
public class 동물 {
    //  public 동물() {}
}
```
```java
public class Driver {
	public static void main(String[] args) {
		동물 뽀로로 = new 동물();
	}
}
```
❗️동물 클래스에는 아무런 메서드도 없는 것 처럼 보임
-> 하지만 하나의 메서드가 존재 (아무런 인자도 갖지 않는 기본 생성자 메서드)

## 인자가 있는 생성자를 갖는 동물
```java
public class 동물 {
    public 동물(String name){
      System.out.println(name);
    }
}
```
```java
public class Driver01 {
	public static void main(String[] args) {
		동물 뽀로로 = new 동물("뽀로로");
	}
}
```
→ 정상적으로 실행

❌ 문제코드 
```java
public class Driver02 {
	public static void main(String[] args) {
		동물 뽀로로 = new 동물("뽀로로");
		동물 무명 = new 동물(); // 컴파일 에러 발생
	}
}
```
→ 컴파일 거부
## 📌 왜 컴파일 거부할까?

- 개발자가 아무런 생성자도 만들지 않으면 자바는 인자가 없는 **기본 생성자를 자동으로 만들어준다.**
- **인자가 있는 생성자를 하나라도 만든다면 자바는 기본 생성자를 만들어 주지 않는다.**

<img src="./image/i24.png " width=550 height=300 />


# 3. 클래스 생성 시의 실행 블록, static 블록

### static 블록이란?
> 클래스가 로딩되고 클래스 변수가 준비된 후 자동으로 실행되는 블록 = 시작프로그램

> 추가로 한 클래스 안에 여러 개의 static 블록이 존재 가능
### 역할은?
> 📌 static 블록은 클래스가 처음 로드될 때 한 번만 실행되기 때문에 보통 클래스 변수 초기화나 클래스에서 필요한 초기화 작업을 수행하는 데에 사용

- Driver01
```java
public class Driver01 {
    public static void main(String[] args) {
        동물 뽀로로 = new 동물();
    }
}
```
- 동물
```java
public class 동물 {
    static {
        System.out.println("동물 클래스 준비");
    }
}
```
→ 결과 
```java
 동물 클래스 준비
```

### static 블록 예시

```java
public class Driver01 {
    public static void main(String[] args) {
        System.out.println("메인 시작");
    }
}
```
→ ❌ 위와 같은 코드를 실행했을 때, 아래와 같은 결과가 나올 것이라 예상할 수 있다. 
```java
 동물 클래스 준비
 메인 시작
```
→ 결과는 '메인 시작'만 출력된다. 
-  '동물' 클래스를 사용하는 코드가 없어서 동물 클래스의 static 블록이 실행되지 않기 때문이다.

### static 블록 예시2

```java
public class Driver02 {
    public static void main(String[] args) {
        System.out.println("메인 시작");
        동물 뽀로로 = new 동물();
    }
}
```
→ 결과
```java
메인 시작
동물 클래스 준비
```

### static 블록 예시3
```java

public class Driver02 {
    public static void main(String[] args) {
        System.out.println("메인 시작");
        동물 뽀로로 = new 동물();
        동물 코끼리 = new 동물();
    }
}
```
→ 결과
```java
메인 시작
동물 클래스 준비
```
> 📌 동물 클래스의 인스턴스로 여러 개 만들어도 동물클래스의 static 블록은 한 번만 실행된다.
### static 블록 예시4
```java
public class Driver05 {
    public static void main(String[] args) {
        System.out.println("main 메서드 시작");
        System.out.println(Animal.age);
    }

}

class Animal {
    static int age = 0;
    static {
        System.out.println("Animal 클레스 시작");
    }
}
```

→ 결과
```java
main 메서드 시작
Animal 클레스 시작
0
```

> 클래스의 정적 속성에 접근할 때에도 static 블록이 싱핼되는 것을 알 수 있다.

클래스가 제일 처음 사용하는 3가지 경우는,

    ① 클래스의 정적 속성을 사용할 때 
    ② 클래스의 정적 메서드를 사용할때 
    ③ 클래스의 인스턴스를 최초로 만들 때 
   

인스턴스 블록도 존재,
- 아무런 표시 없이 {} 블록을 사용
- 인스턴스가 생성될 때마다 실행
- 객체 생성자가 실행 되기 전에 먼저 실행

전체 실행 순서 : static 블록 (순서대로 실행) → 인스턴스 블록 → 생성자


# 4. final 키워드

### Final이란?
> 변수, 메서드, 클래스에서 선언이 가능하며 선언 시 그 필드는 더 이상 수정이 불가능 하다는 의미

### 클래스

```java
public final class A{ }
// final 클래스는 상위 클래스가 될 수 없다.
```
- 상속을 허용하지 않음

### 변수
```java
final static double PI = 3.141592;
// 상수는 한번 초기화 되면 값을 변경할 수 없다.

```
- 변경 뷸가능한 상수가 됨

### 메서드
```java
//Final 메서드일시
    class 클래스명 {
    	final void 메서드(){}
    }
    
    class 클래스명2 extends 클래스명 {
    	void 메서드(){}
    }
    
    //컴파일 에러
    //오버라이딩 금지
```
- 이 메서드를 오버라이딩 못함

# 5. instanceof 연산자

### instanceof 란?
> 인스턴스는 클래스를 통해 만들어진 객체
- instanceof 연산자는 만들어진 객체가 특정 클래스의 인스턴스가 맞는지 확인해주는 연산자
- 실제 객체의 타입의 의해 처리됨.

### 반환값은?
> object가 type이거나 type을 상속받는 클래스라면 true를 리턴하고 아니면 false를 리턴 

📌 객체_참조_변수 instanceof 클래스명

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
→ 실행 결과는 모두 참(true)

→ 펭귄객체 instanceof 동물 가 참인 이유는 "객체 참조 변수 타입"이 아닌 "실제 객체의 타입"에 의해 처리되기 때문!

 ## 📌 "실제 객체의 타입"에 의해 처리??
>"실제 객체의 타입"은 객체를 어떤 클래스의 인스턴스로 생성했는지를 의미한다.

- 위의 예제에서는 동물, 조류, 펭귄 클래스들이 상속 관계에 있다. 

- 이때 펭귄 클래스는 조류 클래스를 상속하고, 조류 클래스는 동물 클래스를 상속한다. 

- 따라서 펭귄 객체는 조류 객체의 인스턴스이기도 하고, 동물 객체의 인스턴스이기도 하다.

- instanceof 연산자는 이런 객체의 상속 관계를 확인할 수 있도록 도와주는 연산자이다. 

- 예를 들어 펭귄객체 instanceof 동물의 결과는 true가 된다. 이는 펭귄 객체가 동물 클래스의 인스턴스이기 때문이다.

- ⭐️ 따라서 "실제 객체의 타입"에 의해 처리된다는 것은, 객체의 상속 관계와 instanceof 연산자를 이용하여 객체가 어떤 클래스의 인스턴스인지 판별한 후, 그에 맞게 처리한다는 것을 의미한다!

# 6. 패키지 [package]

### package란?
> 하나의 클래스 안에서 같은 이름의 클래스들을 사용하기 위한 방법

-  namespace을 만들어주는 역할
```java
package 디렉터리
```
### namespace는 무엇인가?

> 많은 클래스를 다루어야 하는 대규모 프로그램을 작성하는 경우 이름이 같은 클래스를 사용해야 하는 상황이 있다.
 - 이렇게 패키지에 의해 나뉘어진 클래스의 이름의 모임을 일컬어 'namespace' 라고 한다.

# 7. interface 키워드와 implements 키워드

### interface란?
> 다른 클래스를 작성할 때 기본이 되는 틀을 제공하면서, 다른 클래스 사이의 중간 매개 역할까지 담당하는 일종의 추상 클래스를 의미
- interface는 public 추상 메서드와 public 정적 상수만 가질수 있음

```java
interface Speakable{
  double PI = 3.14159;
  final double absoluteZeroPoint = -275.15;

  void sayYes();
}
```

```java
interface Speakable{
  public static final double PI = 3.14159;
   public static final double absoluteZeroPoint = -275.15;

 public abstract void sayYes();
}
```
### 두 코드 동일한 코드이다. 

> 인터페이스는 추상 메서드와 정적 상수만 가질 수 있기에 따로 메서드에 public과, abstract, 속성에 public과 static, final을 붙이지 않아도 자동으로 자바가 알아서 붙여준다.

### sayYes() 메서드의 몸체가 없다! 
```java
interface Speakable{
  double PI = 3.14159;
  final double absoluteZeroPoint = -275.15;

  void sayYes();
}
```
> 추상 메서드는 몸체가 없는 메서드이다. 

## 인터페이스의 변수에 새로운 값을 할당할 수 없다.

```java
public class Driver{
  ...

  public static void test(){
    //에러 발생
    //The final field Speakable.PI cannot be assigned
    Speakable.PI = 3.14;

    //에러 발생
    //The final field Speakable.absoluteZeroPoint
    // cannot be assigned
    Speakable.absoluteZeroPoint = -275.0;
  }
}
```
> "값을 할당할 수 없습니다" 에러 발생 
- 변수에 값을 할당할 수 없다는 것은 상수, 즉 final 변수라는 의미
- 클래스명으로 접근할 수 있는 속성은 정적속성 → 결국 PI와 absoluteZeroPoint는 final static 멤버라는 것

## interface 예제
```java
// 인터페이스 선언
interface Shape {
    double getArea();// 추상 메소드
}

// Shape 인터페이스를 구현한 클래스 선언
class Circle implements Shape {
    double radius;

    public Circle(double radius) {
        this.radius = radius;
    }

    @Override
    public double getArea() {
        return Math.PI * radius * radius;
    }
}
// Shape 인터페이스를 구현한 다른 클래스 선언
class Rectangle implements Shape {
    double width, height;

    public Rectangle(double width, double height) {
        this.width = width;
        this.height = height;
    }

    @Override
    public double getArea() {
        return width * height;
    }
}

public class Main {
    public static void main(String[] args) {
        Shape circle = new Circle(5);
        Shape rectangle = new Rectangle(3, 4);

        System.out.println("Circle Area: " + circle.getArea());
        System.out.println("Rectangle Area: " + rectangle.getArea());
    }
}
```
- Shape 인터페이스는 도형 클래스들이 공통적으로 가져야 하는 getArea() 메서드를 정의하고 있음

- Circle 클래스와 Rectangle 클래스는 각각 Shape 인터페이스를 구현하여 getArea() 메서드를 구현하고 있음
- 이를 이용하여 Main 클래스에서는 각각의 클래스를 Shape 타입으로 선언하여 동일한 메서드를 호출할 수 있음

→ 
**이렇게 인터페이스와 다형성을 이용하면, 도형 클래스의 종류가 늘어나더라도 코드의 수정 없이 쉽게 추가할 수 있다.**


# 8. this 키워드

### this란?
> 인스턴스가 바로 자기 자신을 참조하는 데 사용하는 변수
```java
class test {
	int var = 10;
    
    void test() {
    	int var = 20;
        
        System.out.println(var); // 20
        System.out.println(this.var); // 10
    }
}
```
- 지역 변수와 속성의 이름이 같은 경우 지역 변수가 우선
- 객체 변수와 이름이 같은 지역 변수가 있는 경우 this를 접두사로 사용
- 정적 변수와 이름이 같은 지역 변수가 있는 경우 클래스명을 접두사로 사용


# 9. super 키워드
### super란?
> 상위 클래스의 인스턴스를 지칭
 - 자식 클래스에서 상속받은 부모 클래스의 멤버변수를 참조할때 사용
```java
class Animal {
  String name;

  public Animal(String name) {
    this.name = name;
  }

  public void sayHello() {
    System.out.println("안녕, 나는 " + name + "야.");
  }
}

class Dog extends Animal {
  public Dog(String name) {
    super(name); // 부모 클래스의 생성자 호출
  }

  @Override
  public void sayHello() {
    super.sayHello(); // 부모 클래스의 메서드 호출
    System.out.println("멍멍!");
  }
}

public class Main {
  public static void main(String[] args) {
    Animal animal = new Animal("동물");
    animal.sayHello(); // 출력: 안녕, 나는 동물야.

    Dog dog = new Dog("댕댕이");
    dog.sayHello(); // 출력: 안녕, 나는 댕댕이야. 멍멍!
  }
}
```
> super 키워드를 통해 상위 클래스의 인스턴스 메서드를 호출할 수 있다.
 
 → super.super 형태로 상위의 상위 클래스의 인스턴스에는 접근이 불가능


### Reference
[인스턴스 멤버 this / 정적 멤버 static](https://velog.io/@damhee6624/%EC%9D%B8%EC%8A%A4%ED%84%B4%EC%8A%A4-%EB%A9%A4%EB%B2%84-this-%EC%A0%95%EC%A0%81-%EB%A9%A4%EB%B2%84-static)