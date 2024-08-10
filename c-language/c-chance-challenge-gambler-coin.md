### 제목: C 언어로 구현한 10단계 동전 앞뒷면 맞추기 게임: 도전과 집념의 여정

---

### 서론

컴퓨터 프로그래밍은 문제 해결 능력을 기르는 동시에 창의력을 발휘할 수 있는 흥미로운 도구입니다. 이 아티클에서는 C 언어를 이용하여 재미있고 도전적인 동전 앞뒷면 맞추기 게임을 구현하는 방법을 소개하겠습니다. 이 게임은 10단계로 구성되어 있으며, 각 단계마다 동전의 앞뒷면을 맞추는 단순한 규칙을 가지고 있습니다. 하지만 도중에 틀리면 처음부터 다시 시작해야 하므로, 플레이어는 집념과 인내를 발휘해야 합니다.

### 게임 개요

이 게임의 핵심 목표는 10단계에 걸쳐 동전의 앞뒷면을 맞추는 것입니다. 5단계까지 진행한 후에는 플레이어에게 추가 도전에 대한 선택권이 주어지며, 이 선택에 따라 "Challenge"라는 이름의 새로운 단계로 접어들게 됩니다. 마지막 10단계까지 모두 클리어하면 특별한 메시지가 출력되고 게임이 종료됩니다.

### 주요 기능 및 구현

#### 1. 동전 던지기와 맞추기
게임의 각 단계에서 동전이 가상으로 던져집니다. 동전은 50% 확률로 앞면 또는 뒷면이 나오며, 플레이어는 이를 맞춰야 합니다. 맞추면 다음 단계로 넘어가고, 틀리면 게임은 처음부터 다시 시작됩니다.

#### 2. 단계별 진행
1단계부터 5단계까지는 "단계"로 명명되며, 6단계부터는 "Challenge"라는 새로운 용어를 사용합니다. 5단계를 클리어한 후 플레이어는 "세계의 이치를 깨부수고 확률로서 세상에 도전할 것인가?"라는 질문을 받게 되며, 여기서 yes를 선택하면 Challenge 1(6단계)로 넘어갑니다. no를 선택하면 게임이 종료됩니다.

#### 3. 도전과 실패
Challenge 1부터 5까지는 게임의 후반부로, 매우 긴장감 있는 부분입니다. 이 단계에서 플레이어가 틀리면 "그대는 이치를 극복하지 못했다..."라는 메시지가 출력되며, 다시 처음으로 돌아가게 됩니다. 이를 통해 게임의 난이도가 높아지며, 플레이어의 집중력과 인내심을 시험합니다.

#### 4. 최종 메시지
마지막 10단계, 즉 Challenge 5를 클리어하면 "그대는 집념을 보여 이치를 부수었으니.. 이를 기억하여 나아가라!"라는 메시지가 출력됩니다. 플레이어가 yes를 입력하면 게임은 종료됩니다.

### 코드 설명

아래는 이 게임의 C 언어 코드입니다.

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <stdlib.h>
#include <time.h>
#include <string.h>

void toss(int stage);
void checkResult(int coinState, int stage);
void finalMessage();
void resetGame();

int main()
{
    int command;
    srand(time(0)); // 랜덤 시드 설정

    while (1)
    {
        printf("명령어를 입력하세요 (1: '던져! 던져!', 2: '종료'): ");
        scanf("%d", &command);

        if (command == 1)
        {
            for (int stage = 1; stage <= 10; stage++)
            {
                toss(stage);

                if (stage == 5)
                {
                    char decision[4];
                    printf("\n세계의 이치를 깨부수고 확률로서 세상에 도전할 것인가? (yes 또는 no): ");
                    scanf("%s", decision);

                    if (strcmp(decision, "no") == 0)
                    {
                        printf("\n그대는 세계의 거대한 이치 속에 잠겨 가라앉았다. 그대의 운 또한 여기까지일지니.. 그대는 규율에 대적하지 못하였구나.\n");
                        break;
                    }
                }
            }
        }
        else if (command == 2)
        {
            printf("게임을 종료합니다.\n");
            break;
        }
        else
        {
            printf("알 수 없는 명령어입니다. 다시 입력하세요.\n");
        }
    }

    return 0;
}

void toss(int stage)
{
    int coinState = rand() % 2; // 0 또는 1 무작위 생성
    checkResult(coinState, stage);
}

void checkResult(int coinState, int stage)
{
    char guess[10];
    const char* stageName = stage <= 5 ? "단계" : "Challenge";

    if (stage > 5)
    {
        printf("\n%s %d: 동전의 앞뒷면을 맞춰보세요 ('앞면' 또는 '뒷면'을 입력하세요): ", stageName, stage - 5);
    }
    else
    {
        printf("\n%d단계: 동전의 앞뒷면을 맞춰보세요 ('앞면' 또는 '뒷면'을 입력하세요): ", stage);
    }

    scanf("%s", guess);

    if ((coinState == 1 && strcmp(guess, "앞면") == 0) ||
        (coinState == 0 && strcmp(guess, "뒷면") == 0))
    {
        printf("정답입니다! 다음 단계로 넘어갑니다.\n");
    }
    else
    {
        if (stage > 5)
        {
            printf("그대는 이치를 극복하지 못했다...\n");
        }
        else
        {
            printf("오답입니다! 다시 처음부터 시작하세요.\n");
        }
        resetGame();
    }

    if (stage == 10)
    {
        finalMessage();
    }
}

void finalMessage()
{
    char decision[4];
    printf("\n그대는 집념을 보여 이치를 부수었으니.. 이를 기억하여 나아가라! (yes를 입력하면 종료): ");
    scanf("%s", decision);
    if (strcmp(decision, "yes") == 0)
    {
        printf("세계의 끝에 도달했다.\n");
        exit(0);
    }
}

void resetGame()
{
    main();
    exit(0);
}
```

### 결론

이 게임은 단순한 규칙을 바탕으로 하지만, 플레이어에게 끈기와 도전 정신을 요구합니다. 특히 5단계를 넘어 Challenge로 진입한 이후에는 긴장감이 더욱 고조됩니다. 이처럼 C 언어를 활용하여 창의적이고 도전적인 게임을 구현해보는 것은 프로그래밍 실력을 향상시키는 데 큰 도움이 됩니다. 간단한 문법 구조, 그러나 흥미로운 제가 구상한 코드를 바탕으로 여러분도 더욱 성장할 수 있다면 좋겠습니다.