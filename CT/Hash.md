# 해시(Hash)
- **해시(Hash)는 입력 데이터를 고정된 길이의 데이터로 변환된 값**을 말한다.
- 다른 말로 '해시 값(Hash value), 해시 코드, 체크섬' 이라고도 한다.
- 이러한 해시는 뒤에서 '해시 함수'에 의해서 얻게 됨
- 데이터의 KEY 값이 해시 함수를 통해서 변환된 간단한 정수
- 이렇게 **정수로 변환된 해시는 배열의 인덱스, 위치, 데이터 값을 저장하거나 검색할 때 활용**된다.
<img width="830" height="294" alt="Image" src="https://github.com/user-attachments/assets/c2313802-329c-483c-ac54-ce9d37e1204c" />

### 자료구조의 특징
- 키(KEY)에 데이터(Value)를 매핑할 수 있는 데이터 구조
- 해시 함수를 통해 키의 데이터를 배열에 저장할 수 있는 주소(인덱스 번호)를 계산
- 키를 통해 저장된 데이터를 빠르게 찾고, 저장 및 탐색 속도가 획기적으로 빨라짐

## 문제 풀이
### [프로그래머스] 완주하지 못한 선수
>완주하지 못한 선수의 이름을 출력

<문제점>       
참가자 목록 중, 선수 이름에 중복이 있을 경우 이를 구분해야하는 문제 발생

<해결방법>    
- `Counter` 활용 참가자 이름별 참가자 수 계산
- 참가자와 완주한자와의 차집합을 통해 완지하지못한자 도출
- `join`을 활용해 리스트 문자열 형태로 정리

#### **Counter 함수**
`Counter`는 파이썬 `collections` 모듈의 **빈도수(횟수) 계산용 딕셔너리**    
iterable(문자열, 리스트 등)이나 키워드 인자를 받아 **각 항목이 몇 번 나왔는지**를 세어 준다.

```python
from collections import Counter

def solution(participant, completion):
    # 참가자이름별 참가자 수 계산
    participant_count = Counter(participant)  # {"tom": 2, "amy": 1}

    # 완주자이름별 완주자 수 계산
    completion_count = Counter(completion)  # {"tom": 1}

    # 차집합 통해 완주하지 못한자 계산
    not_completed = partcipant_count - completion_count  # {"tom": 1, "amy": 1} 두 사람이 남음

    # 남아있는 이름(키)들을 ", "로 이어 붙여 문자열로 만듦
    not_completed_str = ', '.join(list(not_completed.keys()))

    return not_completed_str  # 반환: "tom, amy"
```

### [프로그래머스] 폰켓몬
N마리 중 **N/2마리만 선택**할 수 있을 때, **서로 다른 종류 최대 개수**를 구하는 문제

**풀이**
```python
def solution(nums):
    return min(len(set(nums)), len(nums)//2)
```

**설명**    
- `set(nums)` → 폰켓몬 종류의 고유 개수
- 한 번에 데려갈 수 있는 수는 `len(nums)//2`
- 서로 다른 종류 최대치는 결국 **두 값의 최소값**

**예**   
- `nums = [3, 3, 3, 2, 2, 4]` → 고유 {3,2,4} = 3종, N/2=3 → **3**
- `nums = [3, 3, 3, 2, 2, 2]` → 고유 {3, 2} = 2종, N/2=3 → **2**

### [프로그래머스] 전화번호 목록
>한 번호가 다른 번호의 **접두사**이면 `False`, **접두사가 아니면** `True`

#### **정렬 후 인접 비교**를 활용한 풀이 방법
```python
def solution(phone_book):
    phone_book.sort()  # 전화번호 사전 순 정렬
    for a, b in zip(phone_book, phone_book[1:]):  # 이웃한 두 원소씩 묶어서 순회
        if b.startswith(a):  # 앞 번호 a가 뒷 번호 b의 접두사이면 실패
            return False
    return True
```

#### **why `phone_book.sort()`?**    
`.sort()`는 **파이썬 리스트 전용 제자리(in-place) 정렬 메서드**
- **원본 변경**: 리스트 자체를 정렬하고, 반환값은 `None`
- **기본 기준**: 원소의 **자연 순서**(숫자 크기, 문자열 사전순)
- **안전정렬(stable)**: 값이 같은 원소의 **상대 순서 유지**

**예시**
- 문자열 기준 정렬:
  - 입력: `["119", "97674223", "1195524421", "12"]`
  - 정렬: `["119", "1195524421", "12", "97674223"]`
- 숫자 "값"이 아니라 **문자열**로 비교한다는 점 주의:
  - `["10", "2"]`를 사전순으로 정렬 → `["10", "2"]` (문자 `'1'`이 `'2'`보다 먼저라서)
  - 숫자 크기대로 정렬하고 싶으면: `sorted(["10","2"], key=int) # ["2","10"]`

#### **why `for a, b in zip(phone_book, phone_book[1:])`?**
`zip`은 여러 **iterable**을 같은 인덱스끼리 묶어 주는 파이썬 내장 함수    
결과는 튜프들의 이터레이터이며, **가장 짧은** iterable 길이에 맞춰 멈춘다.

**사용 방식**    
- **병렬 순회**: 두(또는 그 이상) 리스트를 **같은 위치끼리** 동시에 처리
- **쌍 만들기**: 키-값, 앞-뒤 요소 등 **짝지어 작업**하기 쉽다
- **언집(unzip)**: `zip(*pairs)`로 다시 분해 가능

**예시**
```python
# 1) 병렬 순회
names = ['a', 'b', 'c']
socres = [90, 85, 95]
for name, score in zip(names, scores):
    print(name, score)  # a 90 / b 85 / c 95

# 2) 인접 쌍 만들기(전화번호 목록 풀이에서 자주 사용)
nums = [1, 2, 3, 5]
for a, b in zip(nums, nums[1:]):
    print(a, b)  # (1, 2), (2, 3), (3, 5) 

# 3) 언집
pairs = [('x', 1), ('y', 2)]
xs, ys = zip(*pairs)  # xs=('x', 'y'), ys=(1, 2)
```