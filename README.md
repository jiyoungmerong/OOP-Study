# 🐸 OOP-Study (Object - Oriented)

## 📕 스프링 입문을 위한 자바 객체 지향의 원리와 이해

***
본격적인 스프링 학습을 위한 사전 지식, 즉 스프링의 근간이 되는 **객체 지향 4대 특성**, **객체 지향 설계 5원칙**, 스프링에서 많이 활용되고 있는 **디자인 패턴**을 학습하고 이해하는 것.

![책](https://user-images.githubusercontent.com/84395062/235654610-31edcaa8-b46a-451c-abbb-50f0f43e7603.png)

## 👨‍👩‍👧‍👧 CONTRIBUTORS

| <img src="https://user-images.githubusercontent.com/84395062/234909203-dd2cb336-6134-42e3-92a0-0a8cdcdc85f5.png" width=400px alt="서명진" />  | <img src="https://user-images.githubusercontent.com/84395062/234910437-c15e34b7-2e4b-4463-b34e-75eb674df4c8.png" width=400px alt="김자경" />  |  <img src="https://user-images.githubusercontent.com/84395062/234911192-3ba716d5-28b9-41bb-9a71-a4aedf1ff8ac.png" witdth=400px alt="허지영"/>  | <img src="https://user-images.githubusercontent.com/84395062/234911516-d01e43bb-27bd-4222-b485-80707686a591.png" width=400px alt="김수연"/> | <img src="https://user-images.githubusercontent.com/84395062/235310656-697ab52c-1c09-4467-b91b-c37a0053ae38.png" width=400px alt="이지윤" />  |
|:------------------------------------------------------------------------------------------------------------------------------------------:|:------------------------------------------------------------------------------------------------------------------------------------------:|:-------------------------------------------------------------------------------------------------------------------------------------------:|:----------------------------------------------------------------------------------------------------------------------------------------:|:------------------------------------------------------------------------------------------------------------------------------------------:|
|                                                   [서명진](https://github.com/myoungjinseo)                                                   |                                                     [김자경](https://github.com/jkkj0414)                                                     |                                                   [허지영](https://github.com/jiyoungmerong)                                                   |                                                    [김수연](https://github.com/tndusy27)                                                    |                                                     [이지윤](https://github.com/dd-jiyun)                                                     |

---
## 📁 Plan (8 Week)

| 주차      | 학습 범위                       | 진행 여부 ✅ |
|:---------:|:-----------------------------|:---------:|
| **1주차** | Chapter1. 사람을 사랑한 기술       |✅|
|          | Chapter2. 자바와 절차적 / 구조적 프로그래밍      |✅|
| **2주차** | Chapter 3: 자바와 객체 지향         |✅|
| **3주차** | Chapter 4: 자바가 확장한 객체 지향      |
| **4주차** | Chapter 5: 객체 지향 설계 5원칙 - SOLID          |
|          | SOLID - 예제 코드 짜기   |
| **5주차** | Chapter 6: 스프링이 사랑한 디자인 패턴      |
|          | [디자인패턴](https://refactoring.guru/ko/design-patterns) - 예제 코드 리뷰|
| **6주차** | Chapter 7: 스프링 삼각형과 설정 정보     |
| **7주차** | 자바 8 람다와 인터페이스 스펙 변화 |
| **8주차** | 각자 코드 가지고 리팩토링 ( 객체지향적으로 짜보기! ) |
---
## 📚 Items
<details>
<summary>Chapter01: 사람을 사랑한 기술</summary>
<div markdown="1">

- 신기술은 이전 기술의 어깨를 딛고
- 기계어에서 객체 지향 프로그래밍 언어로
    - 기계어-0과 1의 행진 / 너무나 비인간적인 언어
    - 어셈블리어-0과 1의 행진을 벗어나 인간 지향으로 / 기계어 니모닉
    - C 언어-강력한 이식성 / One Source Multi Object Use Anywhere
    - C++ 언어-정말 인간적인 프로그래밍 방법론, 객체 지향
    - 자바 - 진정한 객체 지향 언어
    - 신기술은 이전 기술의 어깨를 딛고 개발자를 위해 발전한다
    - 신기술이 역사 속에서 환영만 받은 것은 아니다
- 짧은 글, 긴 생각
    - UML을 대하는 자세
    - 당신은 CBD, SOA가 어려운가?
    - 객체 지향의 4대 특성을 누군가에게 설명할 수 있는가?
    - 스프링 프레임워크는 사상이면서 또 단일 제품이다
- 책 출간의 변

</div>
</details>

<details>
<summary>Chapter02: 자바와 절차적/ 구조적 프로그래밍</summary>
<div markdown="1">

- 자바 프로그램의 개발과 구동
    - 자바에 존재하는 절차적/구조적 프로그래밍의 유산
    - 다시 보는 main() 메서드: 메서드 스택 프레임
- 변수와 메모리: 변수! 너 어디 있니?
- 블록 구문과 메모리: 블록 스택 프레임
- 지역 변수와 메모리: 스택 프레임에 갇혔어요!
- 메서드 호출과 메모리: 메서드 스택 프레임 2
- 전역 변수와 메모리: 전역 변수 쓰지 말라니까요!
- 멀티 스레드 / 멀티 프로세스의 이해
- STS(또는 이클립스)를 이용해 T 메모리 영역 엿보기
- 정리 - 객체 지향은 절차적/구조적 프로그래밍의 어깨를 딛고
 
</div>
</details>

<details>
<summary>Chapter03: 자바와 객체 지향</summary>
<div markdown="1">

- 객체 지향은 인간 지향이다
- 객체 지향의 4 대 특성 - 캡! 상추다
- 클래스 vs. 객체 = 붕어빵틀 vs. 붕어빵 ???
- 추상화: 모델링 82
    - 추상화는 모델링이다
    - 추상화와 T 메모리
    - 클래스 멤버 vs. 객체 멤버 = static 멤버 vs. 인스턴스 멤버
- 상속: 재사용 + 확장
    - 상속의 강력함
    - 상속은 is a 관계를 만족해야 한다?
    - 다중 상속과 자바
    - 상속과 인터페이스
    - 상속과 UML 표기법
    - 상속과 T 메모리
- 다형성: 사용편의성
    - 오버라이딩? 오버로딩?
    - 다형성과 T 메모리
    - 다형성이 지원되지 않는 언어
- 캡슐화: 정보 은닉
    - 객체 멤버의 접근 제어자
- 참조 변수의 복사
- 정리 - 자바 키워드와 OOP 4 대 특성
 
</div>
</details>

<details>
<summary>Chapter04: 자바가 확장한 객체 지향</summary>
<div markdown="1">

- abstract 키워드 - 추상 메서드와 추상 클래스
- 생성자
- 클래스 생성 시의 실행 블록, static 블록
- final 키워드
    - final과 클래스
    - final과 변수
    - final과 메서드
- instanceof 연산자
- package 키워드
- interface 키워드와 implements 키워드
- this 키워드
- super 키워드
- 예비 고수를 위한 한마디
- 정리 - 자바 키워드와 OOP 확장

</div>
</details>

<details>
<summary>Chapter05: 객체 지향 설계 5원칙 - SOLID</summary>
<div markdown="1">

- SRP - 단일 책임 원칙
- OCP - 개방 폐쇄 원칙
- LSP - 리스코프 치환 원칙
- ISP - 인터페이스 분리 원칙
- DIP - 의존 역전 원칙
- 정리 - 객체 지향 세계와 SOLID

</div>
</details>

<details>
<summary>Chapter06: 스프링이 사랑한 디자인 패턴</summary>
<div markdown="1">

- 어댑터 패턴(Adapter Pattern)
- 프록시 패턴(Proxy Pattern)
- 데코레이터 패턴(Decorator Pattern)
- 싱글턴 패턴(Singleton Pattern)
- 템플릿 메서드 패턴(Template Method Pattern)
- 팩터리 메서드 패턴(Factory Method Pattern)
- 전략 패턴(Strategy Pattern)
- 템플릿 콜백 패턴(Template Callback Pattern - 견본/회신 패턴)
- 스프링이 사랑한 다른 패턴들

</div>
</details>

<details>
<summary>Chapter07: 스프링 삼각형과 설정 정보</summary>
<div markdown="1">

- IoC/DI - 제어의 역전/의존성 주입
    - 프로그래밍에서 의존성이란?
    - 스프링 없이 의존성 주입하기 1 - 생성자를 통한 의존성 주입
    - 스프링 없이 의존성 주입하기 2 - 속성을 통한 의존성 주입
    - 스프링을 통한 의존성 주입 - XML 파일 사용
    - 스프링을 통한 의존성 주입 - 스프링 설정 파일(XML)에서 속성 주입
    - 스프링을 통한 의존성 주입 - @Autowired를 통한 속성 주입
    - 스프링을 통한 의존성 주입 - @Resource를 통한 속성 주입
    - 스프링을 통한 의존성 주입 - @Autowired vs. @Resource vs. 태그
- AOP - Aspect? 관점? 핵심 관심사? 횡단 관심사?
    - 일단 덤벼 보자 - 실전편
    - 일단 덤벼 보자 - 설명편
    - 일단 덤벼 보자 - 용어편
    - 일단 덤벼 보자 - POJO와 XML 기반 AOP
    - AOP 기초 완성 310
- PSA - 일관성 있는 서비스 추상화

</div>
</details>


<details>
<summary>00A: 스프링 삼각형과 설정 정보</summary>
<div markdown="1">

- A.1 URL과 @RequestMapping 연결하기
- A.2 인메모리 DB HSQL 사용하기
- A.3 VO와 MyBatis를 이용한 DAO 구현
- A.4 서비스(Service) 구현
- A.5 목록 구현
- A.6 읽기 구현
- A.7 새 글 구현
- A.8 수정 구현
- A.9 삭제 구현
- A.10 리팩터링

</div>
</details>


<details>
<summary>00B: 자바 8 람다와 인터페이스 스펙 변화</summary>
<div markdown="1">

- B.1 람다가 도입된 이유
- B.2 람다란 무엇인가?
- B.3 함수형 인터페이스
- B.4 메서드 호출 인자로 람다 사용
- B.5 메서드 반환값으로 람다 사용
- B.6 자바 8 API에서 제공하는 함수형 인터페이스
- B.7 컬렉션 스트림에서 람다 사용
- B.8 메서드 레퍼런스와 생성자 레퍼런스
- B.9 인터페이스의 디폴트 메서드와 정적 메서드
- B.10 정리

</div>
</details>

## 📝 Guide

### 👨🏻‍💻 Process

1. 서적을 보고 자유롭게 정리
2. 본인 깃허브 이름의 파일에 커밋
3. 발표 전까지 정리한 내용 올리기
4. 전체 세션 때 제비 뽑기로 한 명 발표 → 남은 팀원 질문 👋

### 🔏 Rule
1. 마감 기한 : **매주 목요일** 전체 세션 전까지
2. 질문이 생기면 **바로바로** 질문하기 🙋🏻‍♀️
3. 상의 해야 할 내용 팀원들과 **함께** 😆
4. 실습 과제 시 중간중간 **commit** 해놓기
5. 미제출시 아아 쏘기 ☕️

###  💾 Commit Convention 
❗ 만약 추가하고 싶은 convention이 있으면 공유해주세요 ❗
- **Chapter__**: 진행한 챕터의 제목
- **Feat**: 새로운 기능 추가
- **Fix**: 버그 수정
- **Docs**: 문서 수정
- **Style**: 코드 포맷팅, 세미콜론 누락, 코드 변경이 없는 경우
- **Refactor**: 코드 리펙토링
- **Test**: 테스트 코드, 리펙토링 테스트 코드 추가
- **Chore**: 빌드 업무 수정, 패키지 매니저 수정


### ✍🏻 README.md 작성법
- 해당 주차 책을 공부하면서 알게 된 부분, 중요하다고 생각한 부분이 있다면 정리해 주세요!
    - 개념, 복습, 요약도 모두 좋습니다 😊
- 새롭게 알게 된 사실이나 추가적으로 더 공부한 부분이 있다면 정리해 주세요!
- .md 파일은 mark down 언어로 작성된 파일을 뜻해요
    - [참고] https://gist.github.com/ihoneymon/652be052a0727ad59601#24-코드
