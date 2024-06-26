# 별 모양 삼각형 출력 알고리즘: C 언어 프로그램

이번 아티클에서는 `switch` 문 내 `case 7`에 포함된 별 모양 삼각형을 출력하는 알고리즘을 분석하고, 이를 설명하겠습니다. 또한, `int i, j;` 선언 부분에서 발생할 수 있는 Visual Studio 컴파일러 오류 E1072의 원인도 함께 살펴보겠습니다.

## 알고리즘 설명

`case 7`에 포함된 알고리즘은 1부터 10까지의 숫자를 사용하여 별(*) 모양의 삼각형을 출력하는 프로그램입니다. 이 알고리즘은 중첩된 `for` 루프를 사용하여 별을 출력합니다.

### 코드 설명

다음은 `case 7`에 포함된 코드입니다:

```c
case 7:
    int i, j;
    for (i = 1; i <= 10; i++) {
        for (j = 0; j < i; j++)
            printf("*");
        printf("\n");
    }
    break;
```

### 동작 과정

1. **변수 선언**: `int i, j;`는 반복문에서 사용할 변수 `i`와 `j`를 선언합니다.
2. **외부 `for` 루프**: `for (i = 1; i <= 10; i++)`는 `i`가 1부터 10까지 1씩 증가하며 반복합니다. 이 루프는 총 10번 반복됩니다.
3. **내부 `for` 루프**: `for (j = 0; j < i; j++)`는 `j`가 0부터 `i` 미만까지 반복합니다. 이 루프는 `i`의 값에 따라 반복 횟수가 달라집니다. `i`가 1일 때는 1번, `i`가 2일 때는 2번 반복하는 식입니다.
4. **별 출력**: `printf("*");`는 내부 루프에서 별(*)을 출력합니다. 내부 루프가 끝나면 `printf("\n");`을 사용하여 줄 바꿈을 합니다.
5. **결과**: 최종적으로 별(*) 모양의 삼각형이 출력됩니다.

### 실행 예시

```
*
**
***
****
*****
******
*******
********
*********
**********
```

위 예시는 `case 7`의 알고리즘이 실행된 결과입니다. 각 줄에 출력되는 별의 개수가 1부터 10까지 증가하는 삼각형 모양을 형성합니다.

## Visual Studio 컴파일러 오류 E1072

Visual Studio에서 `int i, j;` 선언 부분에서 E1072 오류가 발생할 수 있습니다. 이는 C89/C90 표준에서는 변수 선언이 블록의 시작 부분에 위치해야 한다는 규칙 때문입니다. `switch` 문의 `case` 레이블 내부에서는 변수를 선언하기 전에 블록을 시작해야 합니다.

### 해결 방법

변수 선언을 블록으로 감싸서 `case` 레이블 내부에 위치하도록 수정해야 합니다:

```c
case 7: {
    int i, j;
    for (i = 1; i <= 10; i++) {
        for (j = 0; j < i; j++)
            printf("*");
        printf("\n");
    }
    break;
}
```

위와 같이 `case 7` 레이블 뒤에 중괄호 `{}`를 추가하여 블록을 형성하면, E1072 오류를 해결할 수 있습니다.

## 결론

이번 아티클에서는 별 모양 삼각형을 출력하는 C 언어 알고리즘을 분석하고 설명하였습니다. 또한, Visual Studio에서 발생할 수 있는 컴파일러 오류 E1072의 원인과 해결 방법을 제시하였습니다. 이러한 알고리즘은 반복문과 조건문의 사용법을 이해하는 데 도움이 되며, 기본적인 출력 패턴을 생성하는 연습에 유용합니다.

