## 첫 코딩 실습

### 개요
이 문서는 파이썬 프로그래밍 입문을 위한 첫 코딩 실습 내용을 정리한 것입니다. 다양한 기본 문법과 함수 사용법을 학습하며, 기초 프로그래밍 능력을 기르기 위한 예제들로 구성되어 있습니다.

### 코드 분석

#### 02장: 출력문과 기본 연산

##### 02-1: 간단한 출력
```python
print('Hello😄')
```
간단한 문자열 출력으로 "Hello😄" 메시지를 출력합니다.

##### 02-2: 여러 개의 출력문
```python
print('친구야~ 안녕~~.')
print('선배님 반가워요.')
print('교수님 안녕하세요.')

print(3 + 5)
print(17 * 234)
print(30 * 4 / 5)
```
문자열과 간단한 산술 연산 결과를 출력합니다.

##### 02-3: 할 일 목록 출력
```python
print('To do list : 2024 - 03 - 15')
print('1. 친구와 점심 식사')
print('2. 영어 회화 공부')
print('3. 영어 발음 훈련')
print('4. C언어 공부')
print('5. 파이썬 정리')
print('6. 잔디 심기')
print('7. 친구들과 채팅')
```
지정된 날짜의 할 일 목록을 출력합니다.

#### 03장: 변수와 문자열

##### 03-1: 변수 선언과 출력
```python
myName = 'J'
myMajor = '컴퓨터공학과'
myName = 'RAY'

print(myName)
print(myMajor)
```
변수를 선언하고 값을 할당한 후 출력합니다.

##### 03-2: 변수 재할당
```python
intro = 'Hello'
print(intro)

intro = '안녕하세요'
print(intro)
```
문자열 변수를 선언하고 값을 재할당한 후 출력합니다.

##### 03-3: 변수 타입 변경
```python
var = 10
print(var)
var = 'Hello Python'
print(var)
```
같은 변수에 다른 타입의 값을 할당한 후 출력합니다.

##### 03-4: 반복 출력
```python
add = 'Good morning!★Δ'
print(add)
print(add)
print(add)
```
같은 문자열을 여러 번 출력합니다.

#### 04장: 데이터 타입과 형변환

##### 04-1: 변수 타입 확인과 변환
```python
var1 = 777
var2 = '777'
var3 = 3.14

var1 = var1 + 1

print(var1)
print(var2)
print(var3)

flag = True
print(flag)

print('--------------------')

print(type(var1))
print(type(var2))
print(type(var3))
print(type(flag))

var2 = int(var2)
print(var2 + 1)
print(type(var2))

var4 = ''
print(type(var4))
var4 = bool(var4)
print(var4)
```
변수의 타입을 확인하고 형변환을 수행합니다.

#### 05장: 입력과 출력

##### 05-1: 사용자 입력 처리
```python
print('[데이터 입력]')
userData = int(input('정수를 입력하세요 : '))
print(userData + 2)
print(type(userData))
```
사용자로부터 정수를 입력받아 연산 후 출력합니다.

##### 05-2: 숫자 입력 처리
```python
userData = int(input('숫자 입력: '))
print(userData + 1)
```
입력된 숫자에 1을 더한 값을 출력합니다.

##### 05-3: 문자열 입력 처리
```python
userName = input('이름을 입력하세요: ')
print('사용자 이름')
print(userName)

userAge = input('나이를 입력하세요: ')
print('사용자 나이')
print('나이: ' + userAge + '살')
```
사용자로부터 이름과 나이를 입력받아 출력합니다.

##### 05-4: 회원 정보 입력
```python
print('회원 정보를 입력하세요')
userName = input('이름 : ')
userMail = input('메일 : ')
userId = input('아이디 : ')
userPw = input('비밀번호 : ')

print('-------------------------------------------------------------------')
print('To.  ' + userMail)
print('▶ 아이디 및 비밀번호 확인')
print(userName + ' 고객님 안녕하세요.')
print(userName + ' 고객님의 아이디와 비밀번호는 아래와 같습니다.')
print('아이디 :  ' + userId)
print('비밀번호 :  ' + userPw)
print('-------------------------------------------------------------------')
```
회원 정보를 입력받아 확인 메일 형식으로 출력합니다.

#### 06장: 기본 연산 및 계산기

##### 06-1: 분기 매출 계산
```python
sales1 = int(input('1월 매출 : '))
sales2 = int(input('2월 매출 : '))
sales3 = int(input('3월 매출 : '))
total = sales1 + sales2 + sales3
print('1분기 전체 매출 : ' + str(total) + '원')
```
1월, 2월, 3월의 매출을 입력받아 1분기 전체 매출을 계산합니다.

##### 06-2: 분기 수익 계산
```python
sales = int(input('1분기 매출 : '))
purchase = int(input('1분기 매입 : '))
profit = sales - purchase
print('수익 : ', profit, '원')
```
매출과 매입을 입력받아 수익을 계산합니다.

##### 06-3: 직사각형 넓이 계산
```python
print('-' * 30)
width = int(input('가로 길이 : '))
length = int(input('세로 길이 : '))
area = width * length
print('넓이 :', area, '㎠')
print('-' * 30)
```
가로와 세로 길이를 입력받아 직사각형의 넓이를 계산합니다.

##### 06-4: BMI 계산
```python
weight = float(input('몸무게(kg) : '))
height = float(input('신장(m) : '))
bmi = weight / height**2
print('BMI :', bmi)
```
몸무게와 신장을 입력받아 BMI를 계산합니다.

#### 07장: 조건문

##### 07-1: 복리 계산
```python
myMoney = 5000000
rate = 0.05

myMoney += myMoney * rate
myMoney += myMoney * rate
myMoney += myMoney * rate
myMoney += myMoney * rate
myMoney += myMoney * rate

print('5년 후 총 수령액 : ', int(myMoney), '원')
```
초기 금액에 매년 5%의 이자를 적용하여 5년 후의 총 수령액을 계산합니다.

##### 07-2: 키에 따른 놀이기구 탑승 가능 여부
```python
height = int(input('어린이의 신장을 입력하세요: '))
str = '탑승 가능' if height >= 120 and height < 170 else '탑승 불가능'
print(str)
```
입력받은 키에 따라 놀이기구 탑승 가능 여부를 출력합니다.

##### 07-3: 수입과 지출에 따른 흑자/적자 판별
```python
incoming = int(input('수입 : '))
outgoing = int(input('지출 : '))
result = '흑자' if incoming > outgoing else '적자'
print(result)
```
수입과 지출을 비교하여 흑자 또는 적자를 출력합니다.

#### 08장: 제어문

##### 08-1: 속도 위반 판별
```python
carSpeed = int(input('자동차의 현재 속도는 : '))
if carSpeed >= 50:
    print('속도 위반!!')
```
자동차의 속도를 입력받아 속도 위반 여부를 출력합니다.

##### 08-2: 숫자 비교
```python
num = int(input('숫자를 입력하세요: '))
if num > 10:
    print('num은 10보다 크다.')
print('num:', num)
```
입력받은 숫자가 10보다 큰지 판별합니다.

##### 08-3: 점수에 따른 합격/불합격 판별
```python
score = int(input('점수를 입력하세요: '))
if score >= 80:
    print('합격입니다.')
else:
    print('아쉽습니다. 다시 도전해주세요.')
```
점수를 입력받아 합격 여부를 출력합니다.

##### 08-4: 기계 온도에 따른 팬 가동
```python
temp = int(input('기계 온도를 입력하세요: '))
if temp >= 40:
    print('팬(Fan)가동')
    print('기계 온도가 40도 이상입니다.')
else:
    print('팬(Fan)중지')
    print('기계 온도가 40도 미만입니다.')
```
기계의 온도를 입력받아 팬의 가동 여부를 출력합니다.

#### 09장: 추가 조건문 예제

##### 09-1: 마일리지 사용 가능 여부
```python
mileage = 1200
if mileage >= 1000

:
    print('마일리지를 사용할 수 있습니다.')
else:
    print('마일리지를 사용할 수 없습니다.')
```
마일리지가 1000 이상인지 판별합니다.

##### 09-2: 연산과 조건문 결합
```python
myMoney = 10000
applePrice = 2000
bananaPrice = 3000

numOfApples = myMoney // applePrice
print('구입 가능한 사과의 갯수:', numOfApples)
```
현재 돈으로 구입 가능한 사과의 개수를 계산합니다.

##### 09-3: 기온에 따른 외출 복장 제안
```python
temp = int(input('기온을 입력하세요: '))
if temp >= 30:
    print('반바지를 추천합니다.')
elif temp >= 20:
    print('가벼운 옷을 추천합니다.')
elif temp >= 10:
    print('자켓을 추천합니다.')
else:
    print('외투를 추천합니다.')
```
기온을 입력받아 적절한 외출 복장을 추천합니다.

#### 10장: 연습 문제

##### 10-1: 할인 가격 계산
```python
price = int(input('가격을 입력하세요: '))
if price >= 20000:
    discount = 0.1
elif price >= 10000:
    discount = 0.05
else:
    discount = 0

final_price = price * (1 - discount)
print('할인된 가격:', int(final_price), '원')
```
가격을 입력받아 할인된 최종 가격을 계산합니다.

##### 10-2: 나이별 티켓 가격
```python
age = int(input('나이를 입력하세요: '))
if age < 8:
    price = 500
elif age < 14:
    price = 1000
elif age < 20:
    price = 1500
else:
    price = 2000

print('티켓 가격:', price, '원')
```
나이에 따라 티켓 가격을 출력합니다.

##### 10-3: 양수/음수 판별
```python
num = int(input('숫자를 입력하세요: '))
if num > 0:
    print('양수입니다.')
elif num < 0:
    print('음수입니다.')
else:
    print('0입니다.')
```
입력받은 숫자가 양수, 음수, 0인지 판별합니다.

##### 10-4: 짝수/홀수 판별
```python
num = int(input('숫자를 입력하세요: '))
if num % 2 == 0:
    print('짝수입니다.')
else:
    print('홀수입니다.')
```
입력받은 숫자가 짝수인지 홀수인지 판별합니다.

### 결론
이 문서에서 소개된 코딩 실습 예제들은 파이썬 프로그래밍의 기본 문법과 함수 사용법을 학습하는데 유용합니다. 각 예제를 통해 변수 선언, 입력 및 출력, 조건문, 반복문 등의 기본 개념을 익힐 수 있습니다. 이러한 기초를 탄탄히 다진 후, 더 복잡한 프로그래밍 문제에 도전할 수 있습니다.