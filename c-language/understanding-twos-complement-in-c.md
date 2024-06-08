# C 프로그래밍에서 2의 보수 표현 이해하기

2의 보수는 이진수에 대한 수학적 연산으로, 컴퓨터에서 부호 있는 정수를 나타내는 가장 일반적인 방법입니다. 이는 산술 회로 설계를 단순화하고 양수와 음수를 일관되게 처리할 수 있도록 합니다. 이 글에서는 주어진 정수를 2의 보수로 변환하는 과정을 C 프로그래밍을 통해 설명하겠습니다.

## 단계별 가이드

아래 코드 조각은 사용자의 정수를 입력받아 1의 보수로 변환하고, 그 다음 2의 보수를 구하는 과정을 보여줍니다.

```c
#include <stdio.h>

int main() {
    int n;
    
    // 사용자로부터 정수 입력 받기
    printf("\n 정수 입력 : ");
    scanf("%d", &n);
    
    // 1의 보수로 변환 (비트 단위로 NOT 연산)
    n = ~n;
    
    // 1을 더하면 2의 보수로 변환
    n++;
    
    // 결과 출력
    printf("\n 2의 보수 = %d", n);
    
    return 0;
}
```

### 코드 설명

1. **정수 입력받기**: `scanf` 함수를 사용하여 사용자가 입력한 정수를 변수 `n`에 저장합니다.
   ```c
   printf("\n 정수 입력 : ");
   scanf("%d", &n);
   ```

2. **1의 보수로 변환**: `~` 연산자를 사용하여 정수 `n`의 모든 비트를 반전시킵니다.
   ```c
   n = ~n;
   ```

3. **2의 보수로 변환**: 1의 보수로 변환된 값에 1을 더하여 2의 보수로 변환합니다.
   ```c
   n++;
   ```

4. **결과 출력**: `printf` 함수를 사용하여 변환된 값을 출력합니다.
   ```c
   printf("\n 2의 보수 = %d", n);
   ```

### 2의 보수의 유용성

2의 보수는 컴퓨터 과학에서 매우 유용합니다. 이는 음수 표현을 단순화하고, 덧셈 및 뺄셈과 같은 산술 연산을 동일한 방식으로 처리할 수 있게 해줍니다. 예를 들어, 양수와 음수를 더할 때 별도의 논리를 필요로 하지 않으며, 단순히 이진 덧셈으로 해결할 수 있습니다.

이 코드 예제는 C 프로그래밍 언어에서 2의 보수를 계산하는 기본적인 방법을 보여줍니다. 이를 통해 2의 보수의 개념을 이해하고, 실무에 적용할 수 있습니다.