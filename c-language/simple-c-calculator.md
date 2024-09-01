## C 언어로 만드는 간단한 계산기 프로그램

### 소개

프로그래밍을 처음 배우는 사람에게 C 언어는 컴퓨터의 동작 원리를 이해하는 데 매우 유용한 언어입니다. 이번 글에서는 C 언어의 기초 개념을 학습할 수 있는 간단한 계산기 프로그램을 소개하겠습니다. 이 프로그램을 통해 C 언어의 기본적인 입력과 출력, 조건문, 반복문, 함수 사용법을 배울 수 있습니다.

### 프로그램 설명

이 프로그램은 사용자로부터 두 개의 숫자와 수행할 연산을 입력받아 결과를 출력하는 간단한 계산기입니다. 더하기, 빼기, 곱하기, 나누기 기능을 제공합니다. 사용자는 반복적으로 연산을 수행할 수 있으며, 0을 입력하면 프로그램이 종료됩니다.

### 코드

아래는 프로그램의 전체 코드입니다.

```c
#include <stdio.h>

// 함수 선언
void printMenu();
float add(float a, float b);
float subtract(float a, float b);
float multiply(float a, float b);
float divide(float a, float b);

int main() {
    float num1, num2, result;
    int choice;
    
    while (1) {
        printMenu(); // 메뉴 출력
        
        printf("원하는 연산을 선택하세요 (1-4) 또는 0을 눌러 종료: ");
        scanf("%d", &choice);
        
        if (choice == 0) {
            printf("프로그램을 종료합니다.\n");
            break;
        }
        
        printf("첫 번째 숫자를 입력하세요: ");
        scanf("%f", &num1);
        printf("두 번째 숫자를 입력하세요: ");
        scanf("%f", &num2);
        
        // 선택된 연산 수행
        switch (choice) {
            case 1:
                result = add(num1, num2);
                printf("결과: %.2f\n", result);
                break;
            case 2:
                result = subtract(num1, num2);
                printf("결과: %.2f\n", result);
                break;
            case 3:
                result = multiply(num1, num2);
                printf("결과: %.2f\n", result);
                break;
            case 4:
                if (num2 != 0) {
                    result = divide(num1, num2);
                    printf("결과: %.2f\n", result);
                } else {
                    printf("오류: 0으로 나눌 수 없습니다.\n");
                }
                break;
            default:
                printf("잘못된 선택입니다. 다시 시도하세요.\n");
                break;
        }
    }
    
    return 0;
}

// 함수 정의
void printMenu() {
    printf("======== 계산기 ========\n");
    printf("1. 더하기\n");
    printf("2. 빼기\n");
    printf("3. 곱하기\n");
    printf("4. 나누기\n");
    printf("=======================\n");
}

float add(float a, float b) {
    return a + b;
}

float subtract(float a, float b) {
    return a - b;
}

float multiply(float a, float b) {
    return a * b;
}

float divide(float a, float b) {
    return a / b;
}
```

### 주요 개념 설명

이 프로그램은 다양한 C 언어의 기본 개념을 포함하고 있습니다. 아래에서 각각의 주요 부분을 설명하겠습니다.

#### 1. 함수 선언 및 정의

프로그램의 상단에는 `printMenu`, `add`, `subtract`, `multiply`, `divide`라는 5개의 함수가 선언되어 있습니다. 이러한 함수들은 각각의 기능을 분리하여 코드의 재사용성과 가독성을 높여줍니다.

- **printMenu**: 메뉴를 출력하여 사용자에게 선택 가능한 연산을 보여줍니다.
- **add, subtract, multiply, divide**: 각각의 연산을 수행하고 결과를 반환하는 함수들입니다.

#### 2. 메인 함수

`main` 함수는 프로그램의 진입점이며, 여기에서 사용자 입력을 처리하고 적절한 연산을 수행합니다.

- **입력 처리**: `scanf` 함수를 사용하여 사용자로부터 연산 종류와 숫자를 입력받습니다.
- **반복문**: `while (1)` 반복문을 통해 사용자가 종료를 선택할 때까지 프로그램이 반복 실행됩니다.
- **조건문**: `switch` 문을 통해 사용자가 선택한 연산에 따라 다른 함수가 호출됩니다.

#### 3. 오류 처리

나누기 연산에서 두 번째 숫자가 0일 경우, 오류 메시지를 출력하고 연산을 중단합니다. 이는 실수를 방지하기 위한 중요한 오류 처리 기법입니다.

### 마무리

이 간단한 계산기 프로그램을 통해 C 언어의 기본 개념을 익힐 수 있습니다. 이 프로그램을 직접 작성하고 실행해 보면서 입출력, 조건문, 반복문, 함수 사용법에 대한 이해를 깊게 할 수 있습니다. 프로그래밍을 처음 시작하는 분들에게 좋은 연습이 될 것입니다.