# itertools
효율적인 루핑을 위한 이터레이터를 만드는 함수
> from itertools import *

`itertools` 라이브러리는 파이썬에서 반복 작업을 효율적으로 수행하기 위한 도구를 제공함.

**루핑(looping)이란 ?**
반복적인 작업을 수행하는 것을 의미   
주어진 조건이나 특정 횟수에 따라 동일한 코드 블록을 여러 번 실행하는 것을 말함

이터레이터를 사용해 데이터를 반복하는 것은 효율적인 루핑(looping)을 위한 방법 중 하나이다.    
**이는 반복 작업을 보다 효율적으로 수행할 수 있도록 도와줌**

> 알고리즘을 풀 때 **조합**과 **순열**을 쉽게 구할 수 있도록 도와줌

**조합(combinations)과 순열(permutations)의 차이**   
1. **조합(combinations)**   
조합은 순서에 상관없이 주어진 요소들 중, 일부를 선택해 조합하는 것을 말함   

2. **순열(permutations)**   
순열은 순서가 중요한 요소들의 모든 가능한 배열을 나열하는 것을 말함   
순열은 선택된 요소들의 순서가 다른 경우, 다른 조합으로 간주

> 조합은 (A, B)와 (B, A)를 동일한 것으로 간주하지만, 순열은 서로 다른 것으로 간주하는 차이가 있음

## itertools 함수
- combinations()
- combinations_with_replacement()
- product()
- permutations()

### 1. combinations(iterable, r)
iterable에서 원소 개수가 r개인 조합 뽑기
```python
from itertools import combinations

lst = [1, 2 ,3]

for i in combinations(lst, 2):  # lst에서 원소 개수가 2개인 모든 조합을 추출
    print(i)

>> (1, 2)
   (1, 3)
   (2, 3)
```

> 입력 iterable이 정렬되어있으면, 조합 튜플이 정렬된 순서로 생성됨

### 2. combinations_with_replacement(iterable, r)
iterable에서 원소 개수가 r개인 중복 조합 뽑기
```python
from itertools import combinations_with_replacement

lst = ['A', 'B', 'C']

for i in combinations_with_replacement(lst, 2):
    print(i)

>> ('A', 'A')
   ('A', 'B')
   ('A', 'C')
   ('B', 'B')
   ('B', 'C')
   ('C', 'C')
```

> `combinations`와 다르게 중복 조합이 포함된 조합을 추출함

### 3. permutations(iterable, r=None) - 순열
iterable에서 원소 개수가 r개인 순열 뽑기
```python
from itertools import permutations

lst = ['A', 'B', 'C']

for i in permutations(lst):  # r을 지정하지 않거나 r=None으로 설정하면 최대 길이의 순열이 리턴됨
    print(i)

>> ('A', 'B', 'C')
   ('A', 'C', 'B')
   ('B', 'A', 'C')
   ('B', 'C', 'A')
   ('C', 'A', 'B')
   ('C', 'B', 'A')
```

### 4. product(*iterables, repeat=1)
여러 iterable의 데카르트곱 리턴   
product는 다른 함수와 달리 여러 인자로 여러 iterable을 넣어줄 수 있고 iterable간의 모든 짝을 지어서 리턴함

```python
from itertools import product

lst1 = ['A', 'B']
lst2 = ['1', '2']

for i in product(lst1, lst2, repeat=1):  # lst1과 lst2의 모든 쌍을 지어 리턴함
    print(i)

>> ('A', '1')
   ('A', '2')
   ('B', '1')
   ('B', '2')

for i in product(lst1, repeat=3):  # product(lst1, lst1, lst1, repeat=1)과 동일한 출력
    print(i)

>> ('A', 'A', 'A')
   ('A', 'A', 'B')
   ('A', 'B', 'A')
   ('A', 'B', 'B')
   ('B', 'A', 'A')
   ('B', 'A', 'B')
   ('B', 'B', 'A')
   ('B', 'B', 'B')
```
`repeat` : 하나의 입력 iterable이 몇 번 반복되는지를 지정해 해당 iterable 요소를 여러 번 사용해 데카르트 곱을 생성할 수 있도록 함   

ex) `itertools.product('AB', repeat=3)` = 'A'와 'B'라는 두개의 요소로 구성된 iterable에서 길이가 3인 모든 조합을 생성