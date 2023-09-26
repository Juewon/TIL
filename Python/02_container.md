# Container(컨테이너) 란?
여러 개의 값을 저장할 수 있는 것(객체)를 의미하며, 서로 다른 자료형을 저장 할 수 있다.

## Contents
- 시퀀스(Sequence)형 컨테이너
- 비 시퀀스(Non-Sequence)형 컨테이너
- 형 변환(TypeCasting)
- 시퀀스형 연산자(Squence Type Operator)

## 컨테이너의 분류
- 시퀀스(Sequence)형 : 순서가 있는(ordered) 데이터
- 비 시퀀스(Non-sequence)형 : 순서가 없는(unordered) 데이터

<center><img src="https://user-images.githubusercontent.com/18046097/61180439-44e60d80-a651-11e9-9adc-e60fa57c2165.png", alt="container"/></center>

## 시퀀스(Sequence)형 컨테이너

### 특징
1. **순서가 있다.** (단, 순서대로 정렬(sort)된것은 아님)
2. **특정 위치의 데이터를 가리킬 수 있다.**

### 종류
- 리스트(list)
- 튜플(tuple)
- 레인지(range)
- 문자형(string)

### 1. 리스트(list)
#### 생성과 접근
- 리스트는 대괄호 `[]` 및 `list()`를 통해 만들 수 있다.
    ```python
    my_list = []
    another_list = list()

    print(my_list, type(my_list))
    print(another_list, type(another_list))
    ```

    ```python
    [] <class 'list'>
    [] <class 'list'>
    ```

#### 수정
- 원하는 위치의 인덱스를 통해 할당(`=`) 연산자로 요소의 수정이 가능
    ```pyhton
    numbers = [1, 2, 3, 4, 5]

    # 수정
    numbers[2] = 30
    print(numbers) 

    # 추가
    numbers.append(6)
    print(numbers)

    # 위치 바꾸기
    numbers[5], numbers[2] = numbers[2], numbers[5]
    print(numbers)

    # 삭제(마지막 요소 삭제)
    numbers.pop()
    print(numbers) 
    ```

    ```python
    [1, 2, 30, 4, 5]
    [1, 2, 30, 4, 5, 6]
    [1, 2, 6, 4, 5, 30]
    [1, 2, 6, 4, 5]
    ```

### 2. 튜플(Tuple)
#### 생성과 접근
- `()`로 묶어서 표현한다.
- tuple은 **수정 불가능(immutable)하다.**
- tuple은 직접 사용하기보다는 파이썬 내부에서 다양한 용도로 활용되고 있다.
    ```pyhton
    my_tuple = (2, 4)
    print(my_tuple, type(my_tuple))
    ```

    ```python
    (2, 4) <class 'tuple'>
    ```
- 변수에 값을 대입하는 방식으로도 튜플이 생성된다.
    ```python
    another_tuple = 2, 4, 10
    print(another_tuple)
    ```

    ```python
    (2, 4, 10)
    ```
- 단일 항목의 경우
  > 하나의 항목으로 구성된 튜플은 생성 시 값 뒤에 쉼표를 붙여야 한다.

  ```python
  single_tuple = (1, )
  print(single_tuple, type(single_tuple))
  ```

  ```python
  (1, ) <class 'tuple'>
  ```

  > 쉼표가 없을경우 값 형식에 따리에 생성됨
  ```python
  x = (1)
  print(x, type(x))
  ```

  ```python
  1 <class 'int'>
  ```

- 튜플 접근 방식
    > 리스트와 접근 방식 똑같음
    ```python
    t = (1, 2, 3)

    t[0], t[-1]
    ```

    ```python
    (1, 3)
    ```

#### 수정
- 튜플은 접근은 가능하지만 데이터 추가/수정/삭제 모두 불가능하다.

### 3. 레인지(range())
`range`는 정수의 시퀀스를 나타내기 위해 사용된다.

1. 기본형 : `range(n)`
    > 0부터 n-1까지의 값을 가짐

2. 범위 지정 : `range(n, m)`
    > n부터 m-1까지의 값을 가짐

3. 범위 및 스텝 지정 : `range(n, m, s)`
    > n부터 m-1까지 +s 만큼 증가함

### 4. 패킹 / 언패킹 연산자(Packing / Unpacking Operator)
모든 시퀀스형(리스트, 튜플 등)은 패킹/언패킹 연산자 `*`를 사용해 객체의 패킹/언패킹이 가능하다.

#### 패킹
- 우변의 객체 수가 좌변의 변수 수보다 많을 경우 객체를 순서대로 대입한다.
- 나머지 항목들은 모두 별 기호로 표시된 변수에 리스트로 대입한다.
    ```python
    x, *y = 1, 2, 3, 4, 5

    print(x, y)
    ```

    ```python
    1 [2, 3, 4, 5]
    ```

#### 언패킹
- argument 이름이 `*`로 시작하는 경우, argument unpacking 이라고 부른다.
- 언패킹의 경우, 튜플 형태로 대입한다.
    ```python
    def multiply(x, y, z):
        return x * y * z
    ```

    ```python
    numbers = [1, 2, 3]
    
    multiply(*numbers)  # multiply(1, 2, 3)
    ```

    ```python
    6
    ```

## 비 시퀀스형(Non-sequence) 컨테이너
### 종류
- 세트(Set)
- 딕셔너리(Dictionary)

### 1. 세트(Set)
- `set`은 순서가 없고 중복된 값이 없는 자료구조이다
- `set`은 수학에서의 집합과 동일하게 처리된다
- `set`은 중괄호 `{}`를 통해 만들며, 객체를 삽입, 변경, 삭제 가능(mutable)하다
- 빈 set를 만들려면 `set()`을 활용한다. (`{}`로 생성 불가)
- 활용 가능한 연산자 : 차집합(`-`), 합집합(`|`), 교집합(`&`)

#### 생성과 접근
```python
s1 = {1, 2, 3}
s2 = {3, 4, 5}
```

- 차집합 (`-`)
```python
s1 - s2

=> {1, 2}
```

- 합집합 (`|`)
```python
s1 | s2

=> {1, 2, 3, 4, 5}
```

- 교집합 : (`&`)
```python
s1 & s2

=> {3}
```

- 중복 제거
```python
s3 = {1, 1, 1, 2, 2, 3}
s3

=> {1, 2, 3}
```

- `set`을 활용해 `list`의 중복된 값을 제거할 수 있다.
- 단, `set`으로 변환하는 순간 순서는 보장할 수 없다.
```python
locations = ['서울', '서울', '대전', '광주', '서울', '대전', '부산', '부산']

list(set(locations))
```
```python
['서울', '광주', '대전', '부산']
```

#### 수정
- 할당 방식이 아닌 메서드로 변경
- `set`는 index가 없어 단일 요소 접근 불가함
```python
s = {1, 2, 3, 2, 1}

# 인덱스가없어 값을 추가하고 삭제함
# 추가
s.add(4)
print(s)

# 삭제
s.remove(2)
print(s)
```
```python
{1, 2, 3, 4}
{1, 3, 4}
```

### 2. 딕셔너리(Dictionary)
`dictionary`는 `key`와 `value`가 쌍으로 이루어져있음

#### 생성과 접근
- `{}` 혹은 `dict()`로 만들 수 있습니다.
- 순서를 보장하지 않음
- `dictionary`에 중복된 `key`는 존재할 수 없다
- `index`가 아닌 `key`값을 통해 `value` 접근 가능
    ```python
    phone_book = {'서울': '02', '경기': '031', '인천': '032', '대전': '042', '광주': '062'}

    phone_book['대전']
    ```
    > '042'

- `dictionary`의 `.keys()` 메소드를 활용해 key를 확인할 수 있다.
    ```pyton
    phone_book.keys()
    ```
    > dict_keys(['서울', '경기', '인천', '대전', '광주'])

- `dictionary`의 `.values()` 메소드를 활용해 value를 확인할 수 있다.
    ```python
    phone_book.values()
    ```
    > dict_values(['02', '031', '032', '042', '062'])

- `dictionary`의 `.items()` 메소드를 활용해 key, value를 확인할 수 있다.
    ```python
    phone_book.items()
    ```
    > dict_items([('서울', '02'), ('경기', '031'), ('인천', '032'), ('대전', '042'), ('광주', '062')])

>`dictionary`의 요소를 추출시 `list` 형태로 나오는것을 확인할 수 있다.

#### dic key는 immutable 자료형만 가능, value는 상관 없음
- number
- bool
- str
- tuple
- range

```python
d = {
    1: 1,
    3.2 : [1, 2, 3],
    'asdf' : 'ASDF',
    (1, 2) : {1, 2, 3},
    range(10) : [1, 2, 3],
}

d
```
```python
=> {1: 1,
    3.2: [1, 2, 3],
    'asdf': 'ASDF',
    (1, 2): {1, 2, 3},
    range(0, 10): [1, 2, 3]}
```

- `dictionary`로 데이터 모음 만들기
    ```python
    # 잘못된 데이터 모음
    data_table1 = {
    '서울': 32,
    '경기': 24,
    '인천': 22,
    }

    # 잘된 데이터 모음
    data_table2 = {
        {'지역': '서울', '수치': 32},
        {'지역': '경기', '수치': 24},
        {'지역': '인천', '수치': 22},
    }
    
    data_table2[2]
    ```
    ```python
    => {'지역': '인천', '수치': 22}
    ```

## 형 변환(TypeCasting)
- 암시적 형 변환(impicit) => 자동
  - 사용자가 의도하지 않고, 파이썬 내부적으로 자료형을 변환하는 경우
    ```python
    # 1. bool type
    print(True + 3)  # 4

    # 2. Numeric type(int, float)
    print(3 + 5.0)  # 8.0 
    ```

- 명시적 형 변환(Explicit) => 의도
  - 사용자가 특정 함수를 활용하여 의도적으로 자료형을 변환하는 경우
  - int
    - str, float => int
    - 단, 형식에 맞는 문자열만 정수로 변환 가능
  - float
    - str, int => float
  - str
    - int, float, list, tuple, dict => str

### 컨테이너형 형 변환
<img width="708" alt="typecasting" src="https://user-images.githubusercontent.com/18046097/61180466-a6a67780-a651-11e9-8c0a-adb9e1ee04de.png">

```python
# 리스트 형변환
l = [1, 2, 3, 4]
print(str(l)) # '[1, 2, 3, 4]'
print(tuple(l)) # (1, 2, 3, 4)
print(set(l)) # {1, 2, 3, 4}
#range(l) # 불가
#dict(l) # 불가

# 튜플 형변환
t = (1, 2, 3, 4)
print(str(t)) # '(1, 2, 3, 4)'
print(list(t)) # [1, 2, 3, 4]
print(set(t)) # {1, 2, 3, 4}
#range(t) # 불가
#dict(t) # 불가

# range 형변환
r = range(1, 5)
print(str(r)) # 'range(1, 5)'
print(list(r)) # [1, 2, 3, 4]
print(set(r)) # {1, 2, 3, 4}
print(tuple(r)) # (1,2,3,4)
#dict(r) # 불가

# set 형변환
s = {1, 2, 3, 4}
print(str(s)) # '{1, 2, 3, 4}'
print(list(s)) # [1, 2, 3, 4]
print(tuple(s)) # {1, 2, 3, 4}
#range(s) # 불가
#dict(s) # 불가

# dict 형변환
d = {'name': 'ssafy', 'year': 2020}
print(str(d)) # "{'name': 'ssafy', 'year': 2020}"
print(list(d)) # ['name', 'year']   => key값만 저장됨
print(tuple(d)) # ('name', 'year')  => key값만 저장됨
print(set(d)) # {'name', 'year'}    => key값만 저장됨
# range(d) 불가
```

## 시퀀스형 연산자(Squence Type Operator)
### 산술 연산자(+)
시퀀스를 연결(concatenation)할 수 있다.
```python
# 두 list 연결 가능
[1, 2] + ['a']  # [1, 2, 'a']

# 두 tuple 연결 가능
(1, 2) + ('a', )  # (1, 2, 'a')

# range에는 사용 불가
range(1) + range(5)  # TypeError
```

### 반복 연산자(*)
시퀀스를 반복 할 수 있다.
```python
# list 반복
[0] * 8  # [0, 0, 0, 0, 0, 0, 0, 0]

# tuple 반복
(1, 2) * 3  # (1, 2, 1, 2, 1, 2)

# range에는 사용 불가
range(1) * 3  # TypeError

# 문자열 반복
'hi' * 3  # 'hihihi'
```