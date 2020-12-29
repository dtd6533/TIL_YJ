# 파이썬 기초

## 자료형(Data Type)

*  파이썬이 처리하는 자료형

  * 정수(int): -1, 0
  * 실수(float): 3.14
  * 문자열(str): '홍길동', "A"
  * 불(bool): True, False

  ```python
  # 정수: int (ctrl+/ -> 주석 설정 및 해제 단축키)
  num = 100
  print("num: ", type(num))
  
  # 실수: float
  PI = 3.14
  print("PI: ", type(PI))
  
  # 문자열: str
  name = '홍길동""'
  print('name: ', type(name))
  
  # 논리: bool
  done = True
  print("done: ", type(done))
  
  # 파이썬에서 변수는 지정된 자료형이 없음(가변 자료형)
  # 저장한 값에 따라 변수의 자료형이 정해짐(동적 타이핑)
  
  a = 100
  print(type(a)) # class int
  
  a = 'hello'
  print(type(a)) # class str
  ```

  ```python
  # 자료형2_형변환 함수
  
  # 형변환함수: 다른 자료형을 지정된 자료형으로 일회성으로 변환시켜주는 함수
  # int(문자열 또는 실수형): 정수형으로 변환
  # float(문자열 또는 정수형): 실수형으로 변환
  # str(정수 또는 실수): 문자열로 변환
  
  # 문자열을 정수로 변환
  print(int('123')) # 정수가 될 수 있는 형태(십진수 형태)만 정수형으로 변환이 가능, print(int('abc'))는 불가능
  # print(int('123.12')) # error: with base 10: '123.12'
  print(int(123.12)) # 소수점 이하 절삭, 123
  print(int(123.99)) # 소수점 이하 절삭, 123
  
  # float() 함수: 문자열 및 정수형을 실수로
  print(float(100)) # 100.0
  print(float('100.123')) # 100.123
  print(float('100')) # 100.0
  
  # 일회성 변환 후 반환
  a = 100
  print(float(a)) # 변수 a가 실수로 바뀌었다는 것을 뜻하는 것은 아님, 여전히 int형
  
  # str(): 정수 또는 실수를 문자열로 변환
  print(type(str(100))) # <class 'str'>
  
  # 입력 코드를 이용한 형변환 이해
  # 사용자로부터 수를 입력받아 그 수의 10 증가한 값을 출력하는 프로그램
  # 키보드를 통해서 입력받는 명령(함수): input()
  # 입력된 숫자를 변수에 저장
  su = int(input("수 1을 입력하세요: ")) # 사용자가 키보드로 입력한 값을 변수 su에 저장
  su += 10 # 사용자가 키보드로 값을 입력하면 문자열로 처리되므로 int 처리 필수
  print('입력한 값에 10을 증가하면: ', su)
  ```

  

## input

```python
# input(): 키보드로부터 입력받은 값을 반환
# 변수 = input() : 입력된 자료형은 문자열
# x = input()
# print(x, type(x))

# 입력받기 전에 프롬프트 문자열(가이드 문자열) 출력
# 변수 = input("프롬프트 문자열")
# 사용자로부터 이름과 나이를 입력받아 입력내용이 맞는지 확인하는 프로그램
name = input("이름을 입력하시오: ")
age = int(input("나이를 입력하시오: "))

print("이름: ", name, "나이: ", age)
```

```python
# 두 수를 입력받아 더한 결과 출력.py
su1 = int(input("숫자 1 입력: "))
su2 = int(input("숫자 1 입력: "))
sum = su1 + su2

print("합: " + str(sum))
```



### eval

```python
# 숫자로 변환하는 함수.py
# int() 정수형으로 변환
int('1123') #1123
# int('123.0') #error

# float() 실수형으로 변환
print(float('123')) #123.0

# eval() 함수: 숫자로 변환
print(eval('123.0')) #123.0
print(eval('123')) #123

# eval() 함수는 수식을 입력하면 해당 수식을 완성해주게 됨
a = eval(input("수식 입력: ")) #3+5
print(a) #8
print(type(a)) #int
```



### 연습문제

* 점수를 입력 받아서 총점과 평균 출력

  ```python
  a = int(input("국어 점수 입력: "))
  eng = int(input("영어 점수 입력: "))
  math = int(input("수학 점수 입력: "))
  total = a + eng + math
  average = (a + eng + math)/3
  print("총점: ", total)
  print("평균: %.2f" % average)
  ```

* 무게와 키 값을 입력 받아서 BMI 지수를 계산하는 프로그램 작성

  ```python
  weight = float(input("몸무게(kg): "))
  height = float(input("키(m): "))
  bmi = weight / height**2
  print("당신의 BMI: %.2f" % bmi)
  ```

* 예금과 이자율 프로그램

  ```python
  deposit = int(input("예금액 입력: "))
  rate = float(input("이자율 입력: "))
  
  interest = int(deposit * rate * 0.01)
  balance = interest + deposit
  
  # 천 단위 구분 없이 출력
  print("예금액: %d" % deposit)
  print("이자율: %.1f%%" % rate)
  print("예금이자: %d원" % interest)
  print("잔액: %d원" % balance)
  
  # 천 단위 구분 출력
  # 쉼표를 붙이면 숫자가 아닌 문자열이 되므로 %s!!!!
  print("예금액: %s" % format(deposit,','))
  print("이자율: %.1f%%" % rate)
  print("예금이자: %s원" % format(int(interest), ','))
  print("잔액: %s원" % format(int(balance), ','))
  ```





## 제어문

* 정상적인 코드 실행 흐름
  * 위 -> 아래 방향으로 실행
* 제어문은 프로그램의 흐름을 제어
* 코드 실행의 흐름을 개발자가 원하는 방향으로 변경할 수 있도록 도와줌



### if

* 조건식이 참이면 주어진 문장 수행

* 조건식이 거짓이면 아무것도 수행하지 않음

  ```python
  # if 1.py
  # if 문은 조건식이 참이면 주어진 문장을 수행
  # 조건식이 거짓이면 아무것도 수행하지 않는다.
  
  # if(조건식):
  #     참일 경우 수행되는 문장
  #     들여쓰기는 Tab키를 이용
  #     들여쓰기 주의 해야 함
  #     위 if문에 걸리는 문장은 들여쓰기 되어있는 라인까지 실행
  
  # 기본예제
  password = 1234
  if password == 1234:
      print('비밀번호가 일치합니다.')
  
  # 기본예제 2
  password = 1234
  if password == 1234:
      print('비밀번호가 일치합니다.')
  print('비밀번호 확인이 끝났습니다.') # 조건식이 참이거나 거짓일 때 모두 수행
  
  # 예제 1. 사용자로부터 비밀번호를 입력받아서 해당 비밀번호가 지정된 비밀번호와 같은 지 확인후 결과 출력
  passinput = input('비밀 번호를 입력하세요: ')
  passsave = '12345'
  
  if passinput == passsave:
      print('비밀번호 일치')
  print('확인 종료')
  ```



### if ~ else

* 조건식이 참이면 if문 수행

* 조건식이 거짓이면 else문 수행

  ```python
  # 조건식이 참이면 if문 수행
  # 조건식이 거짓이면 else문 수행
  passinput = input('비밀 번호를 입력하세요: ')
  passsave = '12345'
  
  if passinput == passsave:
      print('비밀번호 일치')
  else:
      print('비밀번호 불일치')
  
  print('확인 종료')
  
  # 예제 2
  # 사용자가 입력한 비밀번호와 저장된 비밀번호가 일치하지 않으면 불일치라는 문구, 일치하면 다음 문장을 수행
  # 단, if~else 구문을 사용할 것
  passinput = input('비밀 번호를 입력하세요: ')
  passsave = '12345'
  
  if passinput != passsave:
      print('불일치')
  else:
      pass # 어떤 작업도 수행하지 않고 문장을 종료, 값이 일치해서 else 구문으로 왔을 경우 종료시킴
  print('확인 종료')
  ```

  

  #### 연습문제

  * 로그인 프로그램 작성

  ```python
  id = input("아이디 입력: ")
  idsave = 'flower'
  password = input('비밀번호 입력: ')
  passwordsave = '1234'
  
  if (id == idsave) and (password == passwordsave): # 양쪽 조건 모두 확인 
      print("로그인 성공")
  else:
      print("로그인 실패")
  ```

  * 짐의 무게 프로그램

  ```python
  weight = float(input("짐의 무게는 얼마입니까?: "))
  
  if weight > 20:
      print("무게 초과, 수수료 20,000원")
  else:
      print("수수료 없음")
  print("종료합니다.")
  ```

  * 정수의 짝수 여부 확인 프로그램

  ```python
  number = int(input("정수 입력: "))
  if number % 2 == 0:
      print("짝수")
  else:
      print("홀수")
  ```

  

### if ~ elif ~ else

* 또 다른 조건이 있을 때 elif 사용

  ```python
  #1. 사용자가 입력한 정수가 음수, 양수 0인지 판단하는 프로그램
  num = int(input('정수 입력: '))
  
  if num < 0:
      print('음수')
  elif num > 0:
      print('양수')
  else:
      print('0')
      
      
  #2. 정수 3개를 입력 받아서 제일 큰 수를 출력하는 프로그램
  num1 = int(input('정수 1 을 입력하세요.: '))
  num2 = int(input('정수 2 을 입력하세요.: '))
  num3 = int(input('정수 3 을 입력하세요.: '))
  
  if (num1 > num2) and (num1 > num3):
      print('가장 큰 수는 ',  num1)
  elif num2 > num3:
      print('가장 큰 수는 ', num2)
  else:
      print('가장 큰 수는 ', num3)
      
      
  #3. 사용자로부터 점수를 입력받아 해당 점수의 학점을 결정해서 출력하시오.
  # 90 이상은 A, 80 이상은 B, 70 이상 C, 60 이상 D, 60 미만 F로 출력
  # 입력 형식과 출력 형식은 임의로 설정할 것
  
  score = int(input("점수를 입력하시오: "))
  
  if score >= 90:
      print("A")
  elif score >= 80:
      print("B")
  elif score >= 70:
      print("C")
  elif score >= 60:
      print("D")
  else:
      print("F")
  ```

  ### 연습문제

  * 도형을 선택해서 면적 구하기

    ```python
    do = int(input('도형 입력(1: 사각형, 2: 삼각형, 3: 원): '))
    
    if do == 1:
        width = int(input('가로 입력: '))
        height = int(input('세로 입력: '))
        area = width * height
        print('사각형의 면적: ', area)
    
    elif do == 2:
        width = int(input('밑변 입력: '))
        height = int(input('높이 입력: '))
        area = width * height * 0.5
        print('삼각형의 면적: ', area)
    
    elif do == 3:
        radius = int(input('반지름 입력: '))
        area = 3.14 * radius ** 2
        print('원의 면적: ', area)
    
    else:
        print("잘못된 입력입니다")
    ```

  * 가위바위보 게임

    ```python
    hong = input('홍길동 입력: ')
    lee = input('이몽룡 입력: ')
    
    if (hong == '가위') and (lee == '보') or \
        (hong == '바위') and (lee == '가위') or \
         (hong == '보') and (lee == '바위'):
        print('홍길동이 이겼습니다.')
    
    elif hong == lee:
        print('비겼습니다.')
    else:
        print('이몽룡이 이겼습니다.')
    ```

    

    ### 난수

    ```python
    # 파이썬에서 난수(random number) 사용하기 위해서는 모듈(random)을 사용해야 함
    # random 모듈의 randint() 함수를 이용해서 난수를 발생시켜 봄
    # 최소부터 최대 사이의 임의의 정수 반환해주는 함수
    # 모듈을 프로그램 안으로 갖고 와야 함
    # from random import randint
    # n = randint(1,100) -> 1 부터 100 사이에서 임의 숫자(정수) 하나를 반환
    from random import randint
    n = randint(1,100)
    print(n)
    ```

  * 가위바이보 게임을 컴퓨터와 YOU로 변경

    ```python
    # 가위 바위 보 게임을 컴퓨터오 you로 변경
    # 컴퓨터는 랜덤하게 가위바위보를 생성(난수를 이용)
    # 1. 가위 , 2. 바위, 3, 보
    
    #(solution 1). 
    from random import randint
    n = randint(1,3)
    you = input('YOU 입력: ')
    
    if n == 1:
        if you == '바위':
            print('당신이 이겼습니다.')
        elif you == '보':
            print('컴퓨터가 이겼습니다.')
        else:
            print('비겼습니다.')
        print('컴퓨터는 가위입니다.')
    
    elif n == 2:
        if you == '보':
            print('당신이 이겼습니다.')
        elif you == '가위':
            print('컴퓨터가 이겼습니다.')
        else:
            print('비겼습니다.')
        print('컴퓨터는 바위입니다.')
    
    else:
        if you == '가위':
            print('당신이 이겼습니다.')
        elif you == '바위':
            print('컴퓨터가 이겼습니다.')
        else:
            print('비겼습니다.')
        print('컴퓨터는 보입니다.')
        
       
    #(Solution 2).
    from random import randint
    
    n = randint(1, 3)
    you = input('YOU 입력: ')
    if n == 1:
        com = '가위'
    elif n == 2:
        com = '바위'
    else:
        com = '보'
    
    if (com == '가위') and (you == '보') or \
        (com == '바위') and (you == '가위') or \
         (com == '보') and (you == '바위'):
        print('컴퓨터가 이겼습니다.')
    
    elif com == you:
        print('비겼습니다.')
    else:
        print('당신이 이겼습니다.')
    
    print('컴퓨터는 %s 입니다.' % com)
    ```



### 중첩 if

```python
# if 문 안에 다른 if 문이 포함되어 있는 구조
# 사용자로부터 사과 상태를 입력받아서 상태가 '신선'이면 아래 조건에 따라 사과를 구매한다
# 사과가격을 다시 입력받아서 사과 가격이 1000원 미만이면 10개를 산다 출력
# 그렇지 않으면 5개를 산다로 출력
# 사과 상태가 신선이 아니면 사과를 사지 않는다를 출력

apple_quality = input('사과 상태 입력: ')

if apple_quality == '신선':
    apple_price = int(input('사과 가격 입력:'))
    if apple_price < 1000:
        print('10개를 산다.')
    else: 
        print('5개를 산다.')
    
else: 
    print('사과를 사지 않는다.')
```

```python
# 할인 예제
num = int(input('번호 입력(1. 현금, 2. 카드): '))

if num == 1 or num == 2:
    pay = int(input('지불액 입력: '))
    if num == 1:
        print('할인율 10%')
        print('할인액: %d' % (pay * 0.1))
    else:
        print('할인율 5%')
        print('할인액: %d' % (pay * 0.05))

else:
    print('잘못 입력하였습니다. 종료합니다.')
```

```python
# 도형 면적 구하기
do = int(input('도형 입력(1: 사각형, 2: 삼각형, 3: 원): '))

if choice == 1 or choice == 2 or choice == 3
    if do == 1:
        width = int(input('가로 입력: '))
        height = int(input('세로 입력: '))
        area = width * height
        print('사각형의 면적: ', area)
    
    elif do == 2:
        width = int(input('밑변 입력: '))
        height = int(input('높이 입력: '))
        area = width * height * 0.5
        print('삼각형의 면적: ', area)
    
    else:
        radius = int(input('반지름 입력: '))
        area = 3.14 * radius ** 2
        print('원의 면적: ', area)

else:
    print("잘못된 입력입니다")
```



## 반복문

### for

* 정해진 횟수만큼 반복
* `for 변수 in 리스트 또는 범위:`

```python
# for 문은 반복의 횟수가 정해져 있을 때 주로 사용
# for 변수 in 리스트나 범위:
#   반복해야할 문장

# 리스트를 사용한 반복 예제
# 리스트 안에 저장되어 있는 이름을 모두 출력하시오
# 리스트: 여러 개의 데이터가 하나의 공간에 저장되는 구조, [data1, data2, ...]기호를 사용해서 리스트 생성

for name in ['홍길동', '이몽룡', '성춘향', '변학도']:
    print(name)
    
# 리스트에 0~9까지 저장을 하고 해당 리스트의 값을 모두 출력하시오.
for x in [0,1,2,3,4,5,6,7,8,9]:
    print(x)
    
# 위에서 작성한 프로그램을 한 줄에 내용이 모두 출력되도록 변경하시오.
print('--------------------------------------------')
for x in [0,1,2,3,4,5,6,7,8,9]:
    print(x, end='') # 한 줄로 출력 0 1 2 3 4 5 6 7 8 9
    
# 반복 범위 사용: rage() 함수
# range() 함수
# 특정범위의 정수 생성
# range(10): 0 ~ 9가지의 정수(10개/ 시작은 0)

# range(start, stop): start에서 stop-1까지의 정수를 생성
# range(0,10): 0 ~ 9 까지의 정수 

# range(start, stop, step): start에서 stop-1까지 step 간격으로 정수 생성
# range(0,10,2): 0에서 부터 9까지 2씩 증가하면서 정수 생성 0 2 4 6 8

# range(10)을 사용해 범위 생성
for i in range(10): # 0~9
    print(i)
    
# range(start, stop)을 사용해 범위 생성
for i in range(11,21): # 11~20
    print(i)
    
# range(start, stop, step)을 사용해 범위 생성
for i in range(1,11,2): # 1 3 5 7 9
    print(i)
```

* 누적합

  ```python
  # 1부터 10까지 출력하고 1부터 10까지 더한 결과를 마지막에 출력하시오.
  # 누적변수 생성
  sumx = 0
  for x in range(1,11):
      print(x)
      sumx += x
  
  print('1부터 10까지의 합: ', sumx)
  
  # 1부터 100까지 홀수를 출력하고 홀수의 합을 구해서 마지막에 출력하시오
  sumx = 0
  for x in range(1,100,2):
      print(x)
      sumx += x
  
  print('1부터 100까지의 홀수합: ', sumx)
  ```

  