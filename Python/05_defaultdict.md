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
>> defaultdict(<class 'int'>, {'key1' : 0})  # er
```
위와 같이 값을 지정하지 않은 키는 그 값이 0으로 지정된다.


