## C 언어 기초와 실습: 다양한 함수 구현과 활용

### 소개

이번 아티클에서는 C 언어를 사용하여 다양한 함수 구현과 활용 방법을 알아보겠습니다. 여러 가지 함수 예제를 통해 각 함수의 역할과 작동 원리를 분석하고, 이를 초심자들도 이해할 수 있도록 자세히 설명합니다. 이 예제 코드는 다양한 기능을 포함하고 있어 C 언어의 기초를 이해하는 데 큰 도움이 될 것입니다.

### 주요 함수와 알고리즘

#### 1. 등차수열 합 계산 함수

```c
int sum(int a, int b, int c) {
    int hap = 0;
    for (int i = a; i <= b; i = i + c)
        hap += i;
    return hap;
}
```

이 함수는 시작 값 `a`, 마지막 값 `b`, 공차 `c`를 받아 등차수열의 합을 계산합니다. `for` 루프를 사용하여 `a`부터 `b`까지 `c`만큼 증가시키면서 합을 구합니다.

#### 2. 성적 계산 함수

```c
void score(int k, int e, int m, int *t, double *a) {
    *t = k + e + m;
    *a = *t / 3.0;    
}
```

국어(`k`), 영어(`e`), 수학(`m`) 점수를 입력받아 총점(`t`)과 평균(`a`)을 계산합니다. 포인터를 사용하여 함수 외부의 변수 값을 수정합니다.

#### 3. 최대값 찾기 함수

```c
int max(int a, int b, int c) {
    if (a > b) if (a > c) return a;
               else       return c;
    else if (b > c)       return b;
         else             return c;
}
```

세 개의 정수(`a`, `b`, `c`) 중 가장 큰 값을 반환합니다. 중첩된 `if`문을 사용하여 비교합니다.

#### 4. 팩토리얼 계산 함수

```c
double fact() {
    int n; 
    double f = 1;
    printf("\n 팩토리얼 인수 입력 : ");
    scanf("%d", &n);
    for (int i = 1; i <= n; i++)
        f = f * i;
    return f;
}
```

사용자로부터 입력받은 정수 `n`의 팩토리얼을 계산합니다. `for` 루프를 사용하여 `1`부터 `n`까지의 곱을 구합니다.

#### 5. 조합 계산 함수

```c
double comb(int n, int r) {
    double c;
    c = fact2(n) / (fact2(n-r) * fact2(r));
    return c;
}
```

조합(combination) 값을 계산하는 함수입니다. `n`과 `r`을 입력받아 조합을 계산합니다. 팩토리얼을 구하는 별도의 함수(`fact2`)를 사용하여 조합 공식을 구현합니다.

#### 6. 소수 판별 함수

```c
int prime(int n) {
    int i;
    for (i = 2; i < n; i++)
        if (n % i == 0)
            return -1;
    if (i == n) return 1;
}
```

정수 `n`이 소수인지 판별합니다. `2`부터 `n-1`까지의 수로 나눠지지 않으면 소수로 판단합니다.

#### 7. 다양한 계산 함수

```c
void calc_1() {
    int n = 10, r = 20;
    printf("\n 덧셈 결과 = %d", n + r);
    printf("\n 곱셈 결과 = %d", n * r);
}
```

```c
int calc_2() {
    int n = 10, r = 20;
    printf("\n 덧셈 결과 = %d", n + r);
    return n * r;
}
```

```c
void calc_3(int n, int r) {
    printf("\n 덧셈 결과 = %d", n + r);
    printf("\n 곱셈 결과 = %d", n * r);
}
```

```c
int calc_4(int n, int r, int *s, int* m, int* d) {
    *s = n - r; 
    *m = n * r;
    *d = n / r;
    return n + r;
}
```

이 함수들은 다양한 인수와 리턴 타입을 활용하여 덧셈, 곱셈, 뺄셈, 나눗셈을 수행합니다. 인수와 리턴 값의 유무에 따라 다른 유형의 함수 호출을 보여줍니다.

#### 8. 순환 호출을 이용한 함수

```c
int sum(int n) {
    if (n == 1) return 1;
    else        return (n + sum(n-1));
}
```

```c
int fact3(int n) {
    if (n == 1) return 1;
    else        return (n * fact3(n-1));
}
```

재귀 호출을 이용하여 등차수열의 합과 팩토리얼을 계산하는 함수입니다. 재귀 호출은 함수가 자기 자신을 호출하는 방식으로, 종료 조건을 반드시 명시해야 무한 루프에 빠지지 않습니다.

### 메인 함수 설명

메인 함수는 다양한 기능을 사용자에게 제공하기 위해 무한 루프를 사용하여 메뉴를 표시하고, 사용자가 선택한 기능에 따라 적절한 함수를 호출합니다.

```c
void main() {
    int i, menu;
    int s, f, d;
    int k, e, m, tot;  double ave;
    int n, r;

    while (1) { // 무한 루프
        printf("\n\n\n 메뉴 1)등차수열 2)최대값 3)성적 4)팩토리얼 5)조합 6)소수판별 7)덧곱셈 8)순환덧셈 9)종료: ");
        scanf("%d", &menu);
        if (menu == 9) break; // 9번을 선택하면 루프 종료
        switch (menu) {
            case 1: // 등차수열 합 계산
                printf("\n 초항, 말항, 등차 입력 : ");
                scanf("%d%d%d", &s, &f, &d);
                i = sum(s, f, d);
                printf("\n 등차수열 합 = %d", i);
                break;
            case 2: // 최대값 찾기
                printf("\n 정수 3개 입력 : ");
                scanf("%d%d%d", &s, &f, &d);
                i = max(s, f, d);
                printf("\n 입력정수 %d,%d,%d 중에서 최대값 = %d", s, f, d, i);
                break;
            case 3: // 성적 계산
                printf("\n국어 영어 수학성적 입력 : ");
                scanf("%d%d%d", &k, &e, &m);
                score(k, e, m, &tot, &ave);
                printf("\n 총점 = %d, 평균 = %.1lf", tot, ave);
                break;
            case 4: // 팩토리얼 계산
                printf("\n 팩토리얼 결과 = %.0lf", fact());
                break;
            case 5: // 조합 계산
                printf("\n 콤비네이션 정수 2개 입력 : ");
                scanf("%d%d", &n, &r);
                printf("\n\n %dC%d = %lf", n, r, comb(n, r));
                break;
            case 6: // 소수 판별
                printf("\n 정수 입력 : ");
                scanf("%d", &n);
                i = prime(n);
                if (i < 0) printf("\n 입력한 정수는 소수가 아님");
                else       printf("\n 입력한 정수는 소수임");
                break;
            case 7: // 덧셈과 곱셈
                n = 10, r = 20;
                calc_1();
                printf("\n 곱셈결과 = %d", calc_2());
                calc_3(n, r);
                i = calc_4(n, r, &f, &s, &d);
                printf("\n 덧셈결과 = %d", i);
                printf("\n 뺄셈결과 = %d", f);
                printf("\n 곱셈결과 = %d", s);
                printf("\n 나눗셈결과 = %d", d);
                break;
            case 8: // 순환 호출
                printf("\n 입력 : "); scanf("%d", &n);
                i = fact3(n);
                printf("\n 실행결과 = %d", i);
                break;
            default: 
                printf("\n 메뉴선택 오류. 다시 선택하시오...\n\n");
        }
    }
}
```

#### 메뉴 선택 및 동작

1. **메뉴 선택**: 사용자로부터 메뉴 번호를 입력받습니다

.
2. **조건문**: `switch` 문을 사용하여 메뉴 번호에 따라 적절한 함수 호출을 실행합니다.
3. **각 메뉴의 기능**:
    - **등차수열 합 계산**: 초항, 말항, 등차를 입력받아 등차수열 합을 계산합니다.
    - **최대값 찾기**: 세 정수를 입력받아 최대값을 출력합니다.
    - **성적 계산**: 국어, 영어, 수학 점수를 입력받아 총점과 평균을 계산합니다.
    - **팩토리얼 계산**: 입력받은 정수의 팩토리얼을 계산합니다.
    - **조합 계산**: 두 정수를 입력받아 조합 값을 계산합니다.
    - **소수 판별**: 입력받은 정수가 소수인지 판별합니다.
    - **덧셈과 곱셈**: 정수 두 개를 이용하여 다양한 연산을 수행합니다.
    - **순환 호출**: 입력받은 정수에 대해 재귀 호출을 사용하여 팩토리얼을 계산합니다.

이러한 구조를 통해 사용자는 다양한 수학적 연산을 직접 경험하고, C 언어의 기초적인 함수 작성 및 호출 방법을 배울 수 있습니다.