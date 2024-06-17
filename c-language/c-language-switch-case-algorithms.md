### C언어의 switch case문을 활용한 다양한 알고리즘 구현

이번 아티클에서는 C언어의 switch case문을 이용하여 다양한 알고리즘을 구현하는 방법에 대해 다루어 보겠습니다. 각기 다른 8가지의 알고리즘을 switch case문을 통해 선택적으로 실행할 수 있도록 구현합니다. 이를 통해 C언어의 조건문 활용과 여러 가지 기초 알고리즘을 학습할 수 있습니다.

#### 코드 구현

```c
#include <stdio.h>
#include <math.h>

// 함수 선언
int arithmeticSum(int n);
char calculateGrade(int score);
int findMax(int a, int b, int c);
int factorial(int n);
int gcd(int a, int b);
void fahrenheitToCelsius(double f);
void printMultiplicationTable(int n);
void printPrimeNumbers(int n);

int main() {
    int choice, n, a, b, c, score;
    double f;

    printf("원하는 알고리즘을 선택하십시오:\n");
    printf("1. 등차수열 합 계산\n");
    printf("2. 성적 계산\n");
    printf("3. 최대값 찾기\n");
    printf("4. 팩토리얼 계산\n");
    printf("5. 최대공약수(GCD) 구하기\n");
    printf("6. 화씨를 섭씨로 변환\n");
    printf("7. 구구단 출력\n");
    printf("8. 에라토스테네스의 체 알고리즘 (n까지 소수 출력)\n");
    scanf("%d", &choice);

    switch (choice) {
        case 1:
            printf("n의 값을 입력하십시오: ");
            scanf("%d", &n);
            printf("등차수열 합: %d\n", arithmeticSum(n));
            break;
        case 2:
            printf("점수를 입력하십시오: ");
            scanf("%d", &score);
            printf("성적: %c\n", calculateGrade(score));
            break;
        case 3:
            printf("세 정수를 입력하십시오: ");
            scanf("%d %d %d", &a, &b, &c);
            printf("최대값: %d\n", findMax(a, b, c));
            break;
        case 4:
            printf("n의 값을 입력하십시오: ");
            scanf("%d", &n);
            printf("팩토리얼: %d\n", factorial(n));
            break;
        case 5:
            printf("두 정수를 입력하십시오: ");
            scanf("%d %d", &a, &b);
            printf("최대공약수: %d\n", gcd(a, b));
            break;
        case 6:
            printf("화씨 온도를 입력하십시오: ");
            scanf("%lf", &f);
            fahrenheitToCelsius(f);
            break;
        case 7:
            printf("출력할 단을 입력하십시오 (2-9): ");
            scanf("%d", &n);
            printMultiplicationTable(n);
            break;
        case 8:
            printf("n의 값을 입력하십시오: ");
            scanf("%d", &n);
            printPrimeNumbers(n);
            break;
        default:
            printf("잘못된 선택입니다.\n");
    }

    return 0;
}

// 등차수열 합 계산 함수
int arithmeticSum(int n) {
    return n * (n + 1) / 2;
}

// 성적 계산 함수
char calculateGrade(int score) {
    if (score >= 90) return 'A';
    else if (score >= 80) return 'B';
    else if (score >= 70) return 'C';
    else if (score >= 60) return 'D';
    else return 'F';
}

// 세 정수 중 최대값 찾기 함수
int findMax(int a, int b, int c) {
    int max = a;
    if (b > max) max = b;
    if (c > max) max = c;
    return max;
}

// 팩토리얼 계산 함수
int factorial(int n) {
    if (n == 0) return 1;
    else return n * factorial(n - 1);
}

// 최대공약수(GCD) 계산 함수
int gcd(int a, int b) {
    while (b != 0) {
        int temp = b;
        b = a % b;
        a = temp;
    }
    return a;
}

// 화씨를 섭씨로 변환 함수
void fahrenheitToCelsius(double f) {
    double c = (f - 32) * 5 / 9;
    printf("섭씨 온도: %.2lf\n", c);
}

// 구구단 출력 함수
void printMultiplicationTable(int n) {
    if (n < 2 || n > 9) {
        printf("잘못된 입력입니다. 2-9 사이의 값을 입력하십시오.\n");
        return;
    }
    for (int i = 1; i <= 9; ++i) {
        printf("%d x %d = %d\n", n, i, n * i);
    }
}

// 에라토스테네스의 체 알고리즘 함수
void printPrimeNumbers(int n) {
    int isPrime[n + 1];
    for (int i = 0; i <= n; ++i) isPrime[i] = 1;

    for (int p = 2; p * p <= n; ++p) {
        if (isPrime[p] == 1) {
            for (int i = p * p; i <= n; i += p) {
                isPrime[i] = 0;
            }
        }
    }

    printf("소수: ");
    for (int p = 2; p <= n; ++p) {
        if (isPrime[p]) printf("%d ", p);
    }
    printf("\n");
}
```

#### 각 알고리즘의 설명

1. **등차수열 합 계산**
   - 등차수열의 합을 계산하는 함수입니다. n까지의 합을 계산하는 간단한 수학 알고리즘을 사용합니다.

2. **성적 계산**
   - 점수를 입력받아 A, B, C, D, F의 성적으로 변환하는 함수입니다. 기본적인 조건문을 사용하여 성적을 계산합니다.

3. **최대값 찾기**
   - 세 개의 정수를 입력받아 그 중 최대값을 찾는 함수입니다. 간단한 비교 연산을 통해 최대값을 결정합니다.

4. **팩토리얼 계산**
   - 입력받은 수의 팩토리얼을 재귀적으로 계산하는 함수입니다. 재귀 호출을 이용해 팩토리얼을 구합니다.

5. **최대공약수(GCD) 구하기**
   - 두 정수의 최대공약수를 유클리드 호제법을 사용해 구하는 함수입니다. 반복문을 통해 GCD를 계산합니다.

6. **화씨를 섭씨로 변환**
   - 화씨 온도를 입력받아 섭씨 온도로 변환하는 함수입니다. 단순한 수식을 이용해 변환을 수행합니다.

7. **구구단 출력**
   - 사용자가 입력한 단의 구구단을 출력하는 함수입니다. 반복문을 사용해 구구단을 출력합니다.

8. **에라토스테네스의 체 알고리즘 (n까지 소수 출력)**
   - 에라토스테네스의 체 알고리즘을 사용해 n까지의 소수를 찾아 출력하는 함수입니다. 배열을 사용해 소수를 판별합니다.

#### 결론

이 코드 구현은 C언어의 switch case문을 통해 다양한 알고리즘을 선택적으로 실행하는 방법을 보여줍니다. 각 알고리즘은 프로그래밍의 기본 개념을 이해하고 연습하는 데 유용합니다. switch case문을 사용하여 조건에 따라 여러 함수를 호출하고 구현하는 과정은 효율적인 프로그래밍 방법을 학습하는 데 도움이 됩니다.