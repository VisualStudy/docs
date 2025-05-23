# c-variable-scope-explained

C 언어에서 **스코프(Scope)** 는 **변수나 함수가 유효하게 접근 가능한 코드 영역**을 의미합니다. 동일한 이름의 변수가 여러 스코프에서 겹칠 수 있기 때문에, 스코프 개념은 **코드의 가독성과 버그 방지에 필수적인 개념**입니다.

---

## 스코프(Scope)란?

**스코프(scope)** 는 어떤 **식별자(identifier)** 가 **얼마나 넓은 범위에서 사용 가능한지**를 나타냅니다. 즉, 어떤 변수나 함수 이름이 **어디서부터 어디까지 인식되고 접근 가능한지를 결정하는 규칙**입니다.

---

## 스코프의 종류

### 1. 블록 스코프 (Block Scope)

* **정의**: 중괄호 `{}` 로 둘러싸인 블록 내부에서만 유효한 스코프
* **적용 대상**: 지역 변수 (`int x;` 등)
* **메모리**: 일반적으로 스택(stack)에 저장됨
* **예시**:

  ```c
  void func() {
      int x = 10; // x는 이 블록 내에서만 유효
      printf("%d\n", x);
  }
  ```

### 2. 함수 스코프 (Function Scope)

* **정의**: 레이블(label)에만 적용되는 특수한 스코프
* **적용 대상**: `goto` 문에서 사용하는 레이블
* **예시**:

  ```c
  void func() {
      goto end;

  start:
      printf("시작\n");

  end:
      printf("끝\n");
  }
  ```

### 3. 파일 스코프 (File Scope)

* **정의**: 함수 외부에 선언된 전역 변수나 함수에 적용
* **적용 대상**: 전역 변수, 함수 정의
* **예시**:

  ```c
  int count = 0; // 파일 스코프: 이 파일 전체에서 유효

  void increment() {
      count++;
  }
  ```

### 4. 프로그램 전체 스코프 (External Scope)

* **정의**: 여러 파일에 걸쳐 사용되도록 `extern` 키워드로 확장된 스코프
* **적용 대상**: 전역 변수 또는 함수 선언
* **예시**:

  ```c
  // file1.c
  int count = 0;

  // file2.c
  extern int count; // 외부 파일의 변수 사용
  ```

---

## 스코프 중첩과 우선순위

* **내부 스코프의 식별자가 외부 스코프의 식별자를 가린다(Shadowing)**
  예시:

  ```c
  int x = 100;

  void func() {
      int x = 50; // 전역 x를 가림
      printf("%d\n", x); // 출력: 50
  }
  ```

* 필요하다면 전역 변수 접근 시 `::` 같은 연산자는 없으며, 이름을 변경하거나 스코프 구분 명확화를 해야 합니다.

---

## 결론

* C 언어에서 **스코프는 변수 설계의 핵심 요소**입니다.
* 좁은 스코프를 우선적으로 사용하여 **코드 충돌을 줄이고 유지보수성을 높이는 것**이 바람직합니다.
* 전역 변수는 필요한 경우에만 사용하고, 스코프 제한을 위해 `static`이나 `extern`을 적절히 활용하세요.
