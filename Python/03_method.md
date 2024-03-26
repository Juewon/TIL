# 03_Method
> 코딩테스트를 준비하면서 헷갈렸던 메서드들을 정리

Contents
- [03\_Method](#03_method)
  - [1. strip](#1-strip)
  - [2. 대/소문자 변환 메서드](#2-대소문자-변환-메서드)
  - [3. map](#3-map)
    - [map 함수 설명](#map-함수-설명)
    - [람다와 map 함수](#람다와-map-함수)
  - [4. lambda](#4-lambda)
    - [람다(lambda) 함수의 활용 예제](#람다lambda-함수의-활용-예제)
      - [1. filter() 함수와 함께 사용하기](#1-filter-함수와-함께-사용하기)
      - [2. sorted() 함수와 함께 사용하기](#2-sorted-함수와-함께-사용하기)
      - [3. reduce() 함수와 함께 사용하기](#3-reduce-함수와-함께-사용하기)
      - [4. max() 함수와 함께 사용하기](#4-max-함수와-함께-사용하기)

## 1. strip
- `strip()`
  - 문자열의 시작과 끝에서 공백을 제거한 후 반환
  - `()` 안에 특정 값을 넣을 경우, 해당하는 문자열을 제거할 수 있음
  - 양쪽 제거
  ```python
  # 공백 제거
  string = "    abcde   "
  string.strip()

  >>> 'abcde'

  # 특정 문자열 제거
  string = "    abcde   "
  string.strip('c')

  >>> 'abde'
  ```
- `lstrip()`
  - 왼쪽 기준 공백, 원하는 문자열 제거
  ```python
  # 공백 제거
  string = "    abcde   "
  string.lstrip()

  >>> 'abcde    '

  # 특정 문자열 제거
  string = "    oooabcdeooo   "
  string.lstrip('o')

  >>> 'abcdeooo'
  ```
- `rstrip()`
  - 오른쪽 기준 공백, 원하는 문자열 제거
  ```python
  # 공백 제거
  string = "    abcde   "
  string.rstrip()

  >>> '    abcde'

  # 특정 문자열 제거
  string = "    oooabcdeooo    "
  string.rstrip('o') 

  >>> 'oooabcde'   
  ```
  
## 2. 대/소문자 변환 메서드
- `upper()` : 문자열을 대문자로 변환하기
  ```python
  str = 'apple'
  str = str.upper()
  print(str)

  >>> APPLE
  ```
- `lower()` : 문자열을 소문자로 변환하기
  ```python
  str = 'APPLE'
  str = str.lower()
  print(str)

  >>> apple
  ```
- `capitalize()` : 문자열의 첫 글자는 대문자로 나머지는 소문자로 변환하기
  ```python
  str = 'APPLE'
  str = str.capitalize()
  print(str)

  >>> Apple
  ``` 
- `title()` : 문자열의 각 단어의 첫글자를 대문자로 변환하기
  ```python
  str = 'APPLE BANANA CHERRY DURIAN'
  str = str.title()
  print(str)

  >>> Apple Banana Cherry Durian
  ```
- `swapcase()` : 문자열에 있는 모든 문자의 대/소문자를 반대로 변환하기
  ```python
  str = 'aPlLe BaNAnA CHeRrY DUrIaN'
  str = str.swapcase()
  print(str)

  >>> ApLlE bAnaNa chErRy duRiAn
  ```
- `isupper() / islower()` : 문자가 대/소문자인지 확인하는 함수
  - 함수 형태 : `string.isupper() / string.islower()`
  - 반환형 : Bool(True, False)
  - `isupper()`
    - 문자열이 모두 대문자인 경우에만 True를 반환
    - 오직 '알파벳 대문자'인 경우에만 True를 반환, 그렇지 않은 경우 False를 반환
    - ex) 공백, 한글, 알파벳 소문자, 기호 등이 있는 경우 False를 반환
  - `islower()`
    - 문자열이 모두 소문자인 경우에만 True를 반환
    - 오직 '알파벳 소문자'인 경우에만 True를 반환, 그렇지 않은 경우 False를 반환
    - ex) 공백, 한글, 알파벳 대문자, 기호 등이 있는 경우 False를 반환

## 3. map
### map 함수 설명
```python
map(function, iterable)
```

**첫번째 매개변수로는 함수**가 오고   
**두번째 매개변수로는 반복 가능한 자료형(리스트, 튜플 등)**이 온다.

**map 함수의 반환 값**은 map객체이기 때문에 해당 자료형을 **list 혹은 tuple로 형 변환**을 시켜주어야 함

함수의 동작은 **두번째 인자로 들어온 반복 가능한 자료형(리스트나 튜플)을 첫 번째 인자로 들어온 함수에 하나씩 집어넣어서 함수를 수행하는** 함수이다.

### 람다와 map 함수
```python
# map과 lambda

# 일반 함수 이용
def func_mul(x):
  return x * 2

result1 = list(map(func_mul, [5, 4, 3, 2, 1]))
print(result1)

# 람다 함수 이용
result2 = list(map(lambda x : x * 2, [5, 4, 3, 2, 1]))
print(result2)

>> [10, 8, 6, 4, 2]
>> [10, 8, 6, 4, 2]
```

> map 함수와 def를 이용해서 리스트의 값을 변화시킬 수도 있지만   
> 간단하고 일회성 작업이라면 def를 이용할 필요 없이 map함수와 lambda를 이용해 좀 더 유용하게 작업을 할 수 있다.

## 4. lambda
람다 함수의 형태는 다음과 같다 

```python
lambda 인자 : 표현식
```

람다 함수는 `def` 키워드를 사용해 함수를 정의하는 것보다 간결하고 간편한 방식으로 함수를 정의할 수 있다.

```python
def add(x, y):
  return x + y

# 위 함수를 람다로 바꾸기
add = lambda x, y : x + y
```

이제 `add`변수는 람다 함수를 참조한다.

```python
add(2, 3)

>> 5
```

### 람다(lambda) 함수의 활용 예제
#### 1. filter() 함수와 함께 사용하기
`filter()`함수는 시퀀스의 모든 요소 중에서 조건에 맞는 요소만을 반환하는 함수이다. 이 때, `filter()`함수와 함께 람다 함수를 사용해 코드를 간결하게 작성할 수 있다.

**`filter()` 함수와 람다 함수를 사용해 홀수만을 추출하기**
```python
mylist = [1, 2, 3, 4, 5]

mylist2 = list(filter(lambda x : x % 2 == 1, mylist))
print(mylist2)

>> [1, 3, 5]
```

#### 2. sorted() 함수와 함께 사용하기
`sorted()`함수는 시퀀스(리스트, 튜플 등)의 요소를 정렬한 결과를 반환한다. 이 때, `sorted()` 함수와 함께 람다 함수를 사용해 정렬 기준을 지정할 수 있다.

**리스트의 요소를 길이 순으로 정렬하기**
```python
mylist = ['apple', 'banana', 'cherry']

mylist2 = sorted(mylist, key=lambda x : len(x))
print(mylist2)

>> ['apple', 'cherry', 'banana']
```

#### 3. reduce() 함수와 함께 사용하기
`reduce()`함수는 시퀀스(리스트, 튜플 등)의 모든 요소를 누적적으로 계산한 결과를 반환한다. 이 때, `reduce()`함수와 함께 람다 함수를 사용해 계산 방식을 지정할 수 있다.

**리스트의 모든 요소를 곱하기**
```python
from functools import reduce

mylist = [1, 2, 3, 4, 5]

result = reduce(lambda x, y : x * y, mylist)
print(result)

>> 120
```

#### 4. max() 함수와 함께 사용하기
`max()`함수의 key를 사용해서 index(key)와 value 짝의 튜플형태로 이루어진 리스트에서 key와 value 중 어떤것을 기준으로 max값을 구할지 선택하기위한 목적으로 많이 활용된다.

**max() 함수와 람다 함께 사용하기**
```python
arr = [(0,10),(1,14),(2,2),(3,24)]
result = max(arr, key=lambda x : x[1])

# 리스트 내에서 튜플의 첫번째 인자 중 가장 큰 튜플값을 반환하게된다.
print(result)

>> (3, 24)
```