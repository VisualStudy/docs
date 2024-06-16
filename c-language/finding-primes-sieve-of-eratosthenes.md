# 소수 찾기: 에라토스테네스의 체 알고리즘

프로그래밍에서 소수(Prime Number)를 찾는 문제는 알고리즘 학습에 있어서 중요한 주제 중 하나입니다. 이번 아티클에서는 소수를 찾는 효율적인 방법 중 하나인 에라토스테네스의 체(Sieve of Eratosthenes) 알고리즘을 C 언어로 구현하는 방법을 살펴보겠습니다.

## 에라토스테네스의 체 알고리즘

에라토스테네스의 체 알고리즘은 고대 그리스의 수학자 에라토스테네스가 고안한 소수 판별 방법입니다. 이 알고리즘은 2부터 시작하여 특정 숫자의 배수를 제거하는 방식으로 소수를 찾아냅니다. 이렇게 하면 특정 범위 내의 모든 소수를 효율적으로 구할 수 있습니다.

## 코드 설명

다음은 C 언어로 구현한 에라토스테네스의 체 알고리즘입니다.

```c
#include <stdio.h>
#define N 100 // 소수를 찾을 범위의 최대값 정의

int main() {
    int prime[N];
    int i, count = 0;

    for (i = 0; i < N; i++) // 배열 요소에 1 입력(소수로 가정)
        prime[i] = 1;

    prime[0] = prime[1] = 0; // 0과 1은 소수가 아님

    for (i = 2; i < N; i++) { // 2부터 시작
        if (prime[i] == 1) { // 소수인 경우에만 작동
            for (int j = 2; i * j < N; j++) {
                prime[i * j] = 0; // 소수의 배수는 소수가 아님
            }
        }
    }

    for (i = 2; i < N; i++) {
        if (prime[i] == 1) { // i가 소수이면
            printf("%3d ", i);
            count++;
            if (count % 10 == 0) printf("\n"); // 10개씩 출력
        }
    }

    return 0;
}
```

### 동작 과정

1. **배열 초기화**: 먼저 `prime` 배열의 모든 요소를 1로 초기화합니다. 여기서 1은 해당 인덱스가 소수임을 가정하는 의미입니다.
2. **0과 1 제외**: `prime[0]`과 `prime[1]`을 0으로 설정하여 0과 1이 소수가 아님을 명시합니다.
3. **소수 판별**: 2부터 시작하여, 해당 인덱스가 소수이면(i.e., `prime[i] == 1`), 그 숫자의 배수들을 모두 소수가 아닌 것으로 설정합니다.
4. **소수 출력**: 배열을 순회하며 소수인 숫자들을 출력합니다. 10개씩 출력하여 가독성을 높입니다.

### 실행 예시

```
  2   3   5   7  11  13  17  19  23  29
 31  37  41  43  47  53  59  61  67  71
 73  79  83  89  97
```

위 예시는 2부터 97까지의 소수를 출력한 결과입니다. 10개씩 출력하여 보기 쉽게 정리하였습니다.

## 결론

에라토스테네스의 체 알고리즘은 특정 범위 내의 소수를 효율적으로 찾는 방법 중 하나입니다. 이 알고리즘은 소수의 배수를 제거하는 방식으로 작동하여 시간 복잡도를 줄입니다. 이번 아티클에서는 C 언어로 이 알고리즘을 구현하는 방법을 살펴보았습니다. 이를 통해 소수 판별 문제를 효율적으로 해결할 수 있습니다.