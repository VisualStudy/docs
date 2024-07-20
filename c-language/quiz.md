## C 언어로 퀴즈 프로그램 만들기

### 소개

이번 아티클에서는 C 언어를 사용하여 퀴즈 프로그램을 만드는 방법에 대해 다룹니다. 이 프로그램은 총 5개의 문제를 무작위 순서로 제시하며, 사용자가 정답을 맞히면 다음 문제로 넘어갑니다. 만약 오답을 입력하면 모든 문제가 다시 처음부터 출제됩니다. 모든 문제를 맞히면 프로그램이 종료됩니다.

### 코드 설명

프로그램은 `Question` 구조체를 사용하여 문제와 보기를 저장합니다. 문제의 순서를 무작위로 섞기 위해 `shuffle` 함수를 사용하며, `ask_questions` 함수에서 문제를 제시하고 정답 여부를 확인합니다.

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <stdlib.h>
#include <time.h>

// 문제의 총 개수
#define TOTAL_QUESTIONS 5

typedef struct {
    char question[100];
    char options[4][20];
    int correct_option;
} Question;

void shuffle(int* array, int n) {
    if (n > 1) {
        srand(time(NULL));
        for (int i = 0; i < n - 1; i++) {
            int j = i + rand() / (RAND_MAX / (n - i) + 1);
            int t = array[j];
            array[j] = array[i];
            array[i] = t;
        }
    }
}

void ask_questions(Question questions[]) {
    int order[TOTAL_QUESTIONS] = { 0, 1, 2, 3, 4 };
    shuffle(order, TOTAL_QUESTIONS);

    for (int i = 0; i < TOTAL_QUESTIONS; i++) {
        int question_index = order[i];
        int a;

        while (1) {
            printf("%s\n", questions[question_index].question);
            for (int j = 0; j < 4; j++) {
                printf("%d) %s ", j + 1, questions[question_index].options[j]);
            }
            printf("\n");
            scanf("%d", &a);

            if (a == questions[question_index].correct_option) {
                printf("정답! 다음 문제로 넘어갑니다.\n\n");
                break;
            }
            else {
                printf("오답! 다시 생각해보세요.\n");
                printf("모든 문제를 랜덤으로 재배치하여 다시 시작합니다.\n\n\n");
                i = -1;  // 문제를 처음부터 다시 시작
                break;
            }
        }
    }
}

int main(void) {
    Question questions[TOTAL_QUESTIONS] = {
        {"다음 중 생물학적 과일이 아닌 것은?", {"수박", "토마토", "오이", "루바브"}, 4},
        {"다음 중 포유류가 아닌 것은?", {"고양이", "상어", "사람", "코끼리"}, 2},
        {"다음 중 대륙이 아닌 것은?", {"아프리카", "아시아", "유럽", "하와이"}, 4},
        {"다음 중 한국의 수도는?", {"서울", "부산", "대전", "인천"}, 1},
        {"다음 중 바다에 속하지 않는 것은?", {"태평양", "대서양", "흑해", "아마존강"}, 4}
    };

    printf("문제를 시작합니다.\n\n");
    ask_questions(questions);

    printf("모든 문제를 맞췄습니다! 프로그램을 종료합니다.\n");
    return 0;
}
```

### 기능 설명

1. **구조체 정의**:
   ```c
   typedef struct {
       char question[100];
       char options[4][20];
       int correct_option;
   } Question;
   ```
   `Question` 구조체는 질문, 보기, 정답을 저장합니다.

2. **문제 순서 섞기**:
   ```c
   void shuffle(int* array, int n) {
       if (n > 1) {
           srand(time(NULL));
           for (int i = 0; i < n - 1; i++) {
               int j = i + rand() / (RAND_MAX / (n - i) + 1);
               int t = array[j];
               array[j] = array[i];
               array[i] = t;
           }
       }
   }
   ```
   `shuffle` 함수는 배열을 무작위로 섞습니다.

3. **문제 출제 및 정답 확인**:
   ```c
   void ask_questions(Question questions[]) {
       int order[TOTAL_QUESTIONS] = { 0, 1, 2, 3, 4 };
       shuffle(order, TOTAL_QUESTIONS);

       for (int i = 0; i < TOTAL_QUESTIONS; i++) {
           int question_index = order[i];
           int a;

           while (1) {
               printf("%s\n", questions[question_index].question);
               for (int j = 0; j < 4; j++) {
                   printf("%d) %s ", j + 1, questions[question_index].options[j]);
               }
               printf("\n");
               scanf("%d", &a);

               if (a == questions[question_index].correct_option) {
                   printf("정답! 다음 문제로 넘어갑니다.\n\n");
                   break;
               }
               else {
                   printf("오답! 다시 생각해보세요.\n");
                   printf("모든 문제를 랜덤으로 재배치하여 다시 시작합니다.\n\n\n");
                   i = -1;  // 문제를 처음부터 다시 시작
                   break;
               }
           }
       }
   }
   ```
   `ask_questions` 함수는 문제를 제시하고 사용자의 입력을 받아 정답 여부를 확인합니다. 오답일 경우 모든 문제를 다시 시작합니다.

### 결론

이 프로그램은 C 언어를 활용하여 기본적인 퀴즈 게임을 구현하는 예제입니다. 구조체와 무작위 배열 섞기 기능을 사용하여 간단하지만 흥미로운 퀴즈 프로그램을 만들 수 있습니다. 이를 통해 C 언어의 기본적인 구조체 사용법과 랜덤 함수 활용법을 익힐 수 있습니다.