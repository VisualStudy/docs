# switch 문을 사용한 성적 계산 프로그램

프로그래밍에서 조건문을 사용하여 성적을 계산하는 방법은 매우 유용합니다. 이번 아티클에서는 C 언어의 `switch` 문을 사용하여 학생의 출석, 과제, 중간고사, 기말고사 점수를 입력받고, 이를 바탕으로 최종 성적을 계산하는 프로그램을 작성해 보겠습니다.

## 성적 계산 로직

성적을 계산하기 위해 출석, 과제, 중간고사, 기말고사의 점수를 각각 입력받습니다. 각 항목의 점수는 다음과 같이 분배됩니다:

- 출석: 10점
- 과제: 20점
- 중간고사: 30점
- 기말고사: 40점

최종 성적은 100점 만점으로 계산되며, 이를 `switch` 문을 사용하여 등급으로 변환합니다.

## 코드 설명

다음은 C 언어로 작성된 성적 계산 프로그램입니다.

```c
#include <stdio.h>

int main() {
    int p, r, m, f, tot;

    printf("\n 출석을 입력하시오: ");
    scanf("%d", &p);
    while (p < 0 || p > 10) {
        printf("\n 출석을 다시 입력하시오: ");
        scanf("%d", &p);
    }

    printf("\n 과제를 입력하시오: ");
    scanf("%d", &r);
    while (r < 0 || r > 20) {
        printf("\n 과제를 다시 입력하시오: ");
        scanf("%d", &r);
    }

    printf("\n 중간고사 성적을 입력하시오: ");
    scanf("%d", &m);
    while (m < 0 || m > 30) {
        printf("\n 중간고사 성적을 다시 입력하시오: ");
        scanf("%d", &m);
    }

    printf("\n 기말고사 성적을 입력하시오: ");
    scanf("%d", &f);
    while (f < 0 || f > 40) {
        printf("\n 기말고사 성적을 다시 입력하시오: ");
        scanf("%d", &f);
    }

    tot = p + r + m + f; // 100점 만점으로 계산

    switch (tot / 5) {
        case 20: 
        case 19: printf("\n 귀하는 (%d점) A+입니다.", tot); break;
        case 18: printf("\n 귀하는 (%d점) A입니다.", tot); break;
        case 17: printf("\n 귀하는 (%d점) B+입니다.", tot); break;
        case 16: printf("\n 귀하는 (%d점) B입니다.", tot); break;
        case 15: printf("\n 귀하는 (%d점) C+입니다.", tot); break;
        case 14: printf("\n 귀하는 (%d점) C입니다.", tot); break;
        case 13: printf("\n 귀하는 (%d점) D+입니다.", tot); break;
        case 12: printf("\n 귀하는 (%d점) D입니다.", tot); break;
        default: printf("\n 귀하는 (%d점) F입니다.", tot);
    }

    return 0;
}
```

### 동작 과정

1. **출석 점수 입력**: 사용자가 입력한 출석 점수가 0에서 10 사이인지 검사합니다. 범위를 벗어나면 다시 입력받습니다.
2. **과제 점수 입력**: 사용자가 입력한 과제 점수가 0에서 20 사이인지 검사합니다. 범위를 벗어나면 다시 입력받습니다.
3. **중간고사 점수 입력**: 사용자가 입력한 중간고사 점수가 0에서 30 사이인지 검사합니다. 범위를 벗어나면 다시 입력받습니다.
4. **기말고사 점수 입력**: 사용자가 입력한 기말고사 점수가 0에서 40 사이인지 검사합니다. 범위를 벗어나면 다시 입력받습니다.
5. **총점 계산**: 출석, 과제, 중간고사, 기말고사의 점수를 합산하여 총점을 계산합니다.
6. **성적 변환**: `switch` 문을 사용하여 총점을 5로 나눈 몫을 기준으로 성적을 변환하고 출력합니다.

### 실행 예시

```
출석을 입력하시오: 8

과제를 입력하시오: 15

중간고사 성적을 입력하시오: 25

기말고사 성적을 입력하시오: 35

귀하는 (83점) B+입니다.
```

위 예시에서 사용자는 출석 8점, 과제 15점, 중간고사 25점, 기말고사 35점을 입력하였으며, 총점은 83점으로 B+ 등급을 받았습니다.

## 결론

이번 아티클에서는 C 언어의 `switch` 문을 사용하여 성적을 계산하는 방법을 살펴보았습니다. 각 항목의 점수를 입력받아 총점을 계산하고, 이를 등급으로 변환하는 과정을 통해 조건문 사용법을 익힐 수 있습니다. 이러한 프로그래밍 기법은 성적뿐만 아니라 다양한 분야에서 응용할 수 있습니다.