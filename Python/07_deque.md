# deque
`collections` 모듈에 있는 `deque` 클래스는 **이중 연결 리스트(double-ended queue)** 로 구현된 자료구조이다.

이 구조는 양쪽 끝에서의 삽입과 삭제가 빠르고 유연하다.

파이썬의 `deque` 클래스는 스택과 큐의 기능을 모두 제공한다.   

**데큐(deque) 불러오기**   
```python
from collections import deque
```

**deque의 장점**   
- 엄격한 리스트를 만들수 있다.
- 속도가 리스트에 비해 굉장히 빠르다. List = O(n), deque = O(1)
- 큐작업이 훨씬 편해진다.

**큐(queue)에 대한 이해**   
큐는 기본적으로 **선입 선출(FIFO : First In First Out)**구조이다.

## deque 사용하기
```python
from collections import deque
data = [1, 2, 3, 4, 5]
d = deque(data)  # 리스트를 deque로 만들기
print(d)

>> deque([1, 2, 3, 4, 5])
```

## deque 함수 목록
- deque.append(x)
  - deque 오른쪽 끝에 항목 x를 추가함
- deque.appendleft(x)
  - deque 왼쪽 끝에 항목 x를 추가함
- deque.clear()
  - deque의 모든 항목을 제거함
- deque.copy()
  - 원본 deque를 복사해 새로운 deque를 생성함
  - 두 deque개체는 독립적이며, 불변성을 보장함
- deque.count(x)
  - deque에서 항목 x의 개수를 반환함
- deque.extend(iterable)
  - iterable의 모든 항목을 deque의 오른쪽 끝에 추가함
- deque.extendleft(iterable)
  - iterable의 모든 항목을 deque의 왼쪽 끝에 추가함
- deque.index(value, start=None, stop=None)
  - deque에서 주어진 값의 첫번째 발생 위치(인덱스)를 반환함
  - start와 stop 매개변수는 검색 범위를 지정하는데 사용될 수 있음
- deque.insert(index, value)
  - 특정 인덱스에 값을 삽입함
- deque(maxlen=x)
  - deque의 최대 길이를 나타내는 읽기 전용 속성
  - deque의 길이가 maxlen보다 클 때 왼쪽부터 요소가 제거됨
- deque.pop()
  - deque의 오른쪽 끝에 있는 항목을 제거하고 반환함
- deque.popleft()
  - deque의 왼쪽 끝에 있는 항목을 제거하고 반환함
- deque.remove(value)
  - deque에서 첫번째로 나오는 value를 제거함
- deque.reverse()
  - deque의 항목들을 역순으로 바꿈
- deque.rotate(n)
  - deque를 오른쪽으로 n번 회전함
  - n이 음수면 왼쪽으로 회전함