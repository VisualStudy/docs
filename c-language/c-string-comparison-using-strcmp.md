# C 프로그래밍 언어에서 `strcmp()`를 활용한 문자열 비교 프로그램 작성

문자열은 프로그래밍에서 자주 사용되는 데이터 형식입니다. 두 문자열을 비교하여 그들이 동일한지, 혹은 사전순으로 어떤 위치에 있는지를 확인하는 작업은 많은 프로그램에서 필수적입니다. C 언어에서는 `strcmp()` 함수를 사용하여 이러한 문자열 비교 작업을 간단하게 수행할 수 있습니다. 이번 아티클에서는 `strcmp()` 함수를 이용해 두 문자열을 비교하는 간단한 프로그램을 작성하는 방법을 알아보겠습니다.

## `strcmp()` 함수란?

`strcmp()` 함수는 C 언어의 표준 라이브러리 함수로, 두 문자열을 비교합니다. 이 함수는 다음과 같은 방식으로 작동합니다:

- 두 문자열이 같으면 `0`을 반환합니다.
- 첫 번째 문자열이 두 번째 문자열보다 사전적으로 앞에 있으면 음수 값을 반환합니다.
- 첫 번째 문자열이 두 번째 문자열보다 사전적으로 뒤에 있으면 양수 값을 반환합니다.

이제 `strcmp()` 함수를 사용하여 간단한 문자열 비교 프로그램을 작성해 보겠습니다.

## 예제 프로그램

다음은 두 개의 문자열을 입력받아 `strcmp()` 함수를 사용해 비교하고, 그 결과를 출력하는 프로그램입니다:

```c
#include <stdio.h>
#include <string.h>

int main() {
    char str1[100];
    char str2[100];

    // 사용자로부터 첫 번째 문자열 입력 받기
    printf("첫 번째 문자열을 입력하세요: ");
    scanf("%s", str1);

    // 사용자로부터 두 번째 문자열 입력 받기
    printf("두 번째 문자열을 입력하세요: ");
    scanf("%s", str2);

    // 문자열 비교
    int result = strcmp(str1, str2);

    if (result == 0) {
        printf("두 문자열은 같습니다.\n");
    } else if (result < 0) {
        printf("첫 번째 문자열이 두 번째 문자열보다 사전적으로 앞에 있습니다.\n");
    } else {
        printf("첫 번째 문자열이 두 번째 문자열보다 사전적으로 뒤에 있습니다.\n");
    }

    return 0;
}
```

### 프로그램 설명

이 프로그램은 다음과 같은 순서로 작동합니다:

1. **문자열 입력받기**: 
   - 프로그램은 사용자로부터 두 개의 문자열을 입력받습니다. 이를 위해 `scanf()` 함수를 사용하여 문자열을 `str1`과 `str2` 변수에 저장합니다.
   
2. **문자열 비교하기**: 
   - `strcmp(str1, str2)` 함수 호출을 통해 두 문자열을 비교하고, 그 결과를 `result` 변수에 저장합니다.

3. **비교 결과 출력하기**:
   - `result`의 값에 따라 세 가지 경우로 나누어 결과를 출력합니다:
     - `result == 0`: 두 문자열이 동일할 경우, "두 문자열은 같습니다."라는 메시지를 출력합니다.
     - `result < 0`: 첫 번째 문자열이 두 번째 문자열보다 사전적으로 앞에 있을 경우, "첫 번째 문자열이 두 번째 문자열보다 사전적으로 앞에 있습니다."라는 메시지를 출력합니다.
     - `result > 0`: 첫 번째 문자열이 두 번째 문자열보다 사전적으로 뒤에 있을 경우, "첫 번째 문자열이 두 번째 문자열보다 사전적으로 뒤에 있습니다."라는 메시지를 출력합니다.

### 실행 예시

```
첫 번째 문자열을 입력하세요: apple
두 번째 문자열을 입력하세요: banana
첫 번째 문자열이 두 번째 문자열보다 사전적으로 앞에 있습니다.
```

이 예제에서 `"apple"`은 `"banana"`보다 사전순으로 앞에 있기 때문에 해당 메시지가 출력됩니다.

## 결론

이 간단한 프로그램을 통해 `strcmp()` 함수를 사용하여 문자열을 비교하는 방법을 배웠습니다. 이 함수는 두 문자열이 동일한지, 사전순으로 어떤 위치에 있는지를 쉽게 확인할 수 있도록 도와줍니다. `strcmp()` 함수는 다양한 상황에서 문자열 비교를 위해 유용하게 활용될 수 있으며, C 언어의 문자열 처리에서 중요한 도구 중 하나입니다. 이 프로그램을 더 발전시켜 사용자의 요구에 맞게 다양한 문자열 비교 작업을 수행하는 프로그램으로 확장해 볼 수 있습니다.