# Coding Notation Conventions

코딩을 처음 접하거나, 여러 언어를 넘나드는 프로그래머라면 다양한 표기법(Notational Conventions)에 대해 정확히 알고 있는 것이 중요하다. 이 글에서는 컴퓨터 프로그래밍에서 자주 사용되는 표기법들을 총정리해 소개한다.

---

## 1. 카멜 표기법 (Camel Case)

### 예시: `myVariableName`, `totalCount`

* 첫 단어는 소문자로 시작하고, 이어지는 단어들은 대문자로 시작한다.
* 주로 **변수명**, **함수명** 등에 사용됨 (JavaScript, Java, C#, etc.)

---

## 2. 파스칼 표기법 (Pascal Case)

### 예시: `MyClassName`, `CalculateTotal`

* 모든 단어의 첫 글자를 대문자로 작성한다.
* 주로 **클래스명**, **생성자 함수명** 등에 사용됨 (C#, Java, TypeScript 등)

---

## 3. 스네이크 표기법 (Snake Case)

### 예시: `user_name`, `max_value`

* 모든 문자를 소문자로 작성하며, 단어는 밑줄(\_)로 구분한다.
* 주로 **파이썬 변수명**, **C 상수**, **데이터베이스 필드명** 등에 사용

---

## 4. 대문자 스네이크 표기법 (UPPER\_SNAKE\_CASE)

### 예시: `MAX_SIZE`, `DEFAULT_TIMEOUT`

* 모든 문자를 대문자로 작성하며, 단어는 밑줄(\_)로 구분
* 주로 **상수 선언**에 사용

---

## 5. 케밥 표기법 (Kebab Case)

### 예시: `user-name`, `main-header`

* 소문자 단어를 하이픈(-)으로 연결
* HTML 클래스 이름, URL 경로, 파일명 등에 사용됨

---

## 6. 헝가리안 표기법 (Hungarian Notation)

### 예시: `strName`, `iCount`, `btnSubmit`

* 변수의 **자료형 또는 역할**을 접두사로 붙임
* 과거에는 많이 쓰였으나 최근에는 잘 사용하지 않음

---

## 7. 점 표기법 (Dot Notation)

### 예시: `object.property`, `module.function()`

* 객체 또는 모듈 구조에서 하위 항목에 접근할 때 사용
* JavaScript, Python, Java 등 대부분의 언어에서 기본적 접근법

---

## 8. 대괄호 표기법 (Bracket Notation)

### 예시: `arr[0]`, `dict["key"]`

* 배열, 딕셔너리 등 인덱스나 키 기반 데이터 접근 시 사용
* JavaScript, Python, C 등에서 사용됨

---

## 9. 백틱 표기법 (Backtick Notation)

### 예시: \`template \${value}\`, \`command\`

* JavaScript의 템플릿 리터럴, 쉘 명령어 표현 등에 사용
* SQL에서 컬럼이나 테이블명을 감쌀 때도 사용됨 (MySQL)

---

## 10. 슬래시 표기법 (Slash Notation)

### 예시: `GET /users`, `import x from './file.js'`

* URL 경로, 파일 경로, 명령어 인자 등에 사용됨
* RESTful API, 파일 시스템 등

---

## 마무리

표기법은 코드의 **가독성**, **유지보수성**, **일관성**에 직접적인 영향을 준다. 협업 환경이나 특정 언어에서는 반드시 정해진 규칙을 따르는 것이 좋으며, 팀의 스타일 가이드에 맞추어 표기법을 사용하는 습관을 들이자.
