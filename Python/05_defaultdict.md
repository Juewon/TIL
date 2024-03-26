# defaultdict()
주로 **해시** 자료구조 문제를 풀 때 쓰일 수 있는 모듈

`from collections import defaultdict`을 통해 불러올 수 있다.

## 해시(Hash)란?
**해쉬/해시(Hash)** 는 **해시 테이블(Hash Table)** 로 Key와 Value를 매핑해서 데이터를 저장하는 자료구조이다. 

**파이썬에서는 기본적으로 제공되는 딕셔너리 자료형이 해시 테이블과 같은 구조임.**

### 해시의 특징
연산의 평균 시간복잡도가 **O(1)** 로 데이터 저장 및 읽기 처리 속도가 매우 빠름

하지만 worst case인 경우 **O(n)** 의 시간복잡도를 갖는다. 그 이유는 **충돌(Collision)** 때문이다.

> 충돌(Collision) - 여러 개의 키값이 해시 함수를 통해 같은 해시 값을 갖는 경우

## defaultdict() 활용법
defaultdict()은 딕셔너리를 만드는 dict클래스의 서브 클래스이다.

**defaultdict()은 인자로 주어진 객체의 기본값을 딕셔너리값의 초기값으로 지정할 수 있다.**   
숫자, 리스트, 셋 등으로 초기화 할 수 있기 때문에 여러 용도로 사용할 수 있다.

### 1. defaultdict(int)
```python
from collections import defaultdict  # defaultdict import 해주기

int_dict = defaultdict(int)  # 디폴트값이 int인 딕셔너리
int_dict['key1']

int_dict
>> defaultdict(<class 'int'>, {'key1' : 0}) 
```
위와 같이 값을 지정하지 않은 키는 그 값이 0으로 지정된다.

```python
int_dict['key2'] = 'test'
int_dict 

>> defaultdict(<class 'int'>, {'key1' : 0}, {'key2' : 'test'})
```

'key2'에 'test'라는 value를 넣었을땐, 'test'가 들어가는 모습   
defaultdict은 말 그대로 처음 키를 지정할 때 값을 주지 않으면 해당 키에 대한 값을 디폴트 값을 지정하겠다는 의미이다.

### 2. defaultdict(list)
```python
list_dict = defaultdict(list)
list_dict

>> defaultdict(<class 'list'>, {})  # 디폴트값이 list인 딕셔너리 생성

list_dict['key1']
list_dict['key2'] = 'test'
list_dict

# 값을 지정하지 않으면 빈 리스트로 초기화, 값을 지정하면 해당값으로 초기화
>> defaultdict(<class 'list'>, {'key1' : [], 'key2' : 'test'})
```

> defaultdict()은 키의 개수를 세어야하는 상황이나 리스트나 셋의 항목을 정리해야 하는 상황에 적절할것 같다.

## defaultdict() 활용예제
**1. defaultdict(int) 활용예제**   
키의 개수를 세기 위해 활용한 defaultdict()
```python
letters = 'dongdongfather'
letters_dict = defaultdict(int)  # 키에 대한 값이 없으면 값을 0으로 초기화
for letter in letters:
    letters_dict[letter] += 1

letters_dict  
# 키의 개수를 세기 위해 활용한 defaultdict()
>> defaultdict(<class 'int'>, {'d': 2, 'o': 2, 'n': 2, 'g': 2, 'f': 1, 'a': 1, 't': 1, 'h': 1, 'e': 1, 'r': 1})
```

**2. defaultdict(list) 활용예제**
```python
name_list = [('kim', 'sungsu'), ('kang', 'hodong'), ('park', 'jisung'), ('kim', 'yuna'), ('park', 'chanho')]
ndict = defaultdict(list)

for k, v in name_list:  # 리스트의 요소가 튜플이기 때무에 k, v 값으로 할당
    ndict[k].append(v)  # 값이 리스트이기 때문에 append()를 이용해서 항목 추가

ndict

>> defaultdict(<class 'list'>, {'kim': ['sungsu', 'yuna'], 'kang': ['hodong'], 'park': ['jisung', 'chanho']})
```

defaultdict()을 활용해 간단하게 각 성이 가진 이름을 취합할 수 있다.

**3. defaultdict(set) 활용예제**
```python
name_list = [('kim', 'sungsu'), ('kang', 'hodong'), ('park', 'jisung'), ('kim', 'yuna'), ('park', 'chanho'), ('kang', 'hodong')]

nset = defaultdict(set)

for k, v in name_list:
    nset[k].add(v)  # set은 add()를 사용해 항목추가

nset

# 중복되는 튜플값이 있어도 set을 활용해 중복을 제거
>> defaultdict(<class 'set'>, {'kim': {'yuna', 'sungsu'}, 'kang': {'hodong'}, 'park': {'jisung', 'chanho'}})
```


