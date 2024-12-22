## C#의 기본 개념 정리

C#은 Microsoft에서 개발한 개체 지향 프로그래밍 언어로, 코드의 가독성과 유지보수성을 강조하는 현대적인 언어입니다. 이 문서에서는 C#의 핵심 개념인 함수, 클래스, 메서드, 변수, 동적(dynamic), 정적(static)에 대해 정리하겠습니다.

---

### 함수(Function)
함수는 특정 작업을 수행하는 코드 블록입니다. 재사용성과 가독성을 높이기 위해 사용되며, 보통 특정 입력값을 받아 결과를 반환하거나 작업을 수행합니다.

#### 함수의 기본 구조
```csharp
리턴타입 함수이름(매개변수)
{
    // 함수 내용
    return 값;
}
```

#### 예시
```csharp
int Add(int a, int b)
{
    return a + b;
}
```
위의 함수는 두 정수를 입력받아 그 합을 반환합니다.

---

### 클래스(Class)
클래스는 개체 지향 프로그래밍에서 데이터와 메서드를 하나로 묶는 기본 단위입니다. C#에서 클래스는 개체를 생성하기 위한 템플릿 역할을 합니다.

#### 클래스의 기본 구조
```csharp
class 클래스이름
{
    // 멤버 변수
    // 메서드
}
```

#### 예시
```csharp
class Person
{
    public string Name;
    public int Age;

    public void Introduce()
    {
        Console.WriteLine($\"안녕하세요, 제 이름은 {Name}이고, 나이는 {Age}살입니다.\");
    }
}
```
위 클래스는 이름(Name)과 나이(Age)를 멤버 변수로 가지며, 자신을 소개하는 Introduce 메서드를 포함합니다.

---

### 메서드(Method)
메서드는 클래스 내에서 정의된 함수입니다. 메서드는 개체의 동작을 정의하며, 클래스의 멤버 데이터를 조작하거나 특정 작업을 수행합니다.

#### 메서드의 기본 구조
```csharp
접근제한자 리턴타입 메서드이름(매개변수)
{
    // 메서드 내용
    return 값;
}
```

#### 예시
```csharp
public void PrintName()
{
    Console.WriteLine($\"이름: {Name}\");
}
```
위 메서드는 클래스 내부에서 이름을 출력하는 역할을 합니다.

---

### 변수(Variable)
변수는 데이터를 저장하는 공간입니다. 변수는 선언 시 데이터 타입과 함께 정의됩니다.

#### 변수 선언
```csharp
데이터타입 변수이름 = 값;
```

#### 예시
```csharp
int age = 25; // 정수형 변수
string name = \"홍길동\"; // 문자열 변수
bool isAlive = true; // 논리형 변수
```

---

### 동적(Dynamic)과 정적(Static)
C#에서는 데이터나 메서드를 동적으로 또는 정적으로 정의할 수 있습니다.

#### 동적(Dynamic)
- 동적 키워드는 컴파일 시 데이터 타입이 정해지지 않고 런타임에 결정됩니다.
- 유연하지만, 타입 안정성이 떨어져 오류가 발생할 가능성이 있습니다.

##### 예시
```csharp
dynamic value = 10;
value = \"문자열\"; // 런타임에 타입 변경 가능
```

#### 정적(Static)
- 정적 멤버는 클래스 자체에 속하며, 개체를 생성하지 않고 사용할 수 있습니다.
- 모든 개체가 동일한 정적 멤버를 공유합니다.

##### 예시
```csharp
class MathUtils
{
    public static int Add(int a, int b)
    {
        return a + b;
    }
}

int result = MathUtils.Add(3, 5); // 개체 생성 없이 호출
```

---

### 결론
C#은 함수, 클래스, 메서드, 변수 등의 기본 개념을 통해 강력한 개체 지향 프로그래밍을 지원합니다. 동적(dynamic)과 정적(static)의 적절한 사용은 프로그램의 유연성과 효율성을 높이는 데 중요한 역할을 합니다. 이러한 기본 개념을 명확히 이해하고 활용하면, C# 프로그래밍에서 더욱 높은 생산성과 품질을 달성할 수 있습니다.