## 콘솔 미로 게임: 콘로(Conlo)

### 소개

콘로(Conlo)는 콘솔에서 즐길 수 있는 간단한 미로 게임입니다. 이 게임은 사용자가 미로를 탐험하며 목표 지점까지 도달하는 것을 목표로 합니다. 이 글에서는 콘로 게임의 작동 원리와 주요 기능들을 살펴보겠습니다.

### 게임의 목표

콘로 게임의 주 목표는 플레이어가 시작 지점에서 출발해 미로를 탐험하며 목표 지점(End Point)까지 도달하는 것입니다. 각 단계마다 미로의 크기와 난이도가 증가하며, 총 5단계로 구성되어 있습니다.

### 게임 시작하기

게임을 시작하려면 콘솔에서 'start'를 입력합니다. 이후 게임이 시작되며, 각 단계마다 미로의 크기가 커지면서 난이도도 증가합니다. 게임을 종료하고 싶다면 'quit' 또는 'q'를 입력하면 됩니다.

### 미로 생성

미로는 깊이 우선 탐색(Depth-First Search, DFS) 알고리즘을 사용하여 생성됩니다. 초기에는 모든 셀이 벽으로 채워져 있으며, DFS를 통해 경로를 생성하고 벽을 허물어 길을 만듭니다.

```c
void generateMaze(int x, int y)
{
    maze[x][y] = 0;
    // 방향을 무작위로 섞어줌
    int directions[4] = { 0, 1, 2, 3 };
    for (int i = 0; i < 4; i++)
    {
        int r = rand() % 4;
        int temp = directions[i];
        directions[i] = directions[r];
        directions[r] = temp;
    }

    for (int i = 0; i < 4; i++)
    {
        int nx = x + dx[directions[i]] * 2;
        int ny = y + dy[directions[i]] * 2;

        if (nx >= 0 && nx < rows && ny >= 0 && ny < cols && maze[nx][ny] == 1)
        {
            maze[x + dx[directions[i]]][y + dy[directions[i]]] = 0;
            generateMaze(nx, ny);
        }
    }
}
```

### 목표 지점 설정

목표 지점은 BFS(Breadth-First Search) 알고리즘을 사용하여 시작 지점으로부터 최소 거리 이상 떨어진 위치에 설정됩니다. 이를 통해 플레이어가 너무 쉽게 목표 지점에 도달하지 않도록 합니다.

```c
void setEndPoint()
{
    int** distances = createMaze(rows, cols);
    // 모든 거리를 -1로 초기화
    for (int i = 0; i < rows; i++)
    {
        for (int j = 0; j < cols; j++)
        {
            distances[i][j] = -1;
        }
    }

    // BFS를 사용하여 거리 계산
    int* queueX = (int*)malloc(rows * cols * sizeof(int));
    int* queueY = (int*)malloc(rows * cols * sizeof(int));
    int front = 0, rear = 0;

    queueX[rear] = startX;
    queueY[rear] = startY;
    rear++;
    distances[startX][startY] = 0;

    while (front < rear)
    {
        int x = queueX[front];
        int y = queueY[front];
        front++;

        for (int i = 0; i < 4; i++)
        {
            int nx = x + dx[i];
            int ny = y + dy[i];

            if (nx >= 0 && nx < rows && ny >= 0 && ny < cols && maze[nx][ny] == 0 && distances[nx][ny] == -1)
            {
                distances[nx][ny] = distances[x][y] + 1;
                queueX[rear] = nx;
                queueY[rear] = ny;
                rear++;
            }
        }
    }

    // 최소 거리를 만족하는 목표 지점 찾기
    int maxDist = 0;
    for (int i = 0; i < rows; i++)
    {
        for (int j = 0; j < cols; j++)
        {
            if (distances[i][j] >= MIN_DISTANCE && distances[i][j] > maxDist)
            {
                maxDist = distances[i][j];
                endX = i;
                endY = j;
            }
        }
    }

    free(queueX);
    free(queueY);
    freeMaze(distances, rows);
}
```

### 플레이어 이동

플레이어는 방향키(w, a, s, d)를 사용하여 이동합니다. 이동 가능한 경로는 미로 생성 시 확보된 경로로 제한됩니다. 플레이어가 목표 지점에 도달하면 다음 단계로 넘어갑니다.

```c
void movePlayer(char direction)
{
    int newX = playerX, newY = playerY;
    if (direction == 'w') newX--;
    if (direction == 's') newX++;
    if (direction == 'a') newY--;
    if (direction == 'd') newY++;

    if (newX >= 0 && newX < rows && newY >= 0 && newY < cols && maze[newX][newY] == 0)
    {
        setCursorPosition(playerX, playerY);
        printf("□ ");
        playerX = newX;
        playerY = newY;
        setCursorPosition(playerX, playerY);
        printf("P ");
    }
}
```

### 게임 인터페이스

게임은 콘솔 환경에서 실행되며, 커서를 숨기고 필요한 경우에만 표시하여 사용자가 게임을 더 몰입감 있게 즐길 수 있도록 합니다. 또한, 플레이어의 위치와 미로의 현재 상태를 실시간으로 출력합니다.

### 결론

콘로(Conlo)는 간단하지만 흥미로운 콘솔 미로 게임으로, 프로그래밍 초보자들에게는 유익한 학습 자료가 될 수 있으며, 일반 사용자들에게는 재미있는 퍼즐 게임이 될 수 있습니다. 각 단계마다 난이도가 증가하는 미로를 탐험하며, 목표 지점에 도달하는 성취감을 느껴보세요.