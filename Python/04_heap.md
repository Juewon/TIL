# 힙 자료구조
**힙**은 특정한 규칙을 가지는 트리로, **최댓값과 최솟값을 찾는 연산**을 빠르게 하기 위해 고안된 **완전이진트리**를 기본으로 한다.

**힙 속성** : A가 B의 부모노드이면 A의 키값과 B의 키값 사이에는 대소 관계가 성립한다.

- 최소 힙 : 부모 노드의 키값이 자식 노드의 키값보다 항상 작은 힙
- 최대 힙 : 부모 노드의 키값이 자식 노드의 키값보다 항상 큰 힙

![힙구조](./imgs/heap01.png)

이때 키값의 대소 관계는 부모/자식 간에만 성립하고, 형제노드 사이에는 대소 관계가 정해지지 않는다.

## heapq
파이썬 `heapq` 모듈은 (priority queue) 알고리즘을 제공한다.

모든 부모 노드는 그의 자식 노드보다 값이 작거나 큰 이진트리(binary tree)구조이며, 내부적으로 인덱스 0에서 시작해 k번째 원소가 항상 자식 원소들(2k+1, 2k+2) 보다 작거나 같은 **최소 힙**의 형태로 정렬된다.

## 힙(heapq) 함수
- heapq.heappush(heap, item) : item을 heap에 추가
- heapq.heappop(heap) : heap에서 가장 작은 원소를 pop한 후 리턴, 비어있는 경우 IndexError가 호출
- heapq.heapify(x) : 리스트 x를 즉각적으로 **heap**으로 변환 (`O(N)`)

### 힙 생성 & 원소 추가
`heapq` 모듈은 리스트를 최소 힙처럼 다룰 수 있기 때문에 빈 리스트를 생성 후 heapq의 함수를 호출할 때마다 리스트를 인자에 넘겨야 함

heap이라는 빈 리스트를 생성하고, 값 추가하기

```python
import heapq

heap = []
heapq.heappush(heap, 50)
heapq.heappush(heap, 10)
heapq.heappush(heap, 20)

print(heap)

>> [10, 50, 20]
```

이미 생성한 리스트가 있다면, `heapify` 함수를 통해 즉각적으로 힙 자료형으로 변환할 수 있다.

```python
heap2 = [50, 10, 20]
heapq.heapify(heap2)

print(heap2)

>> [10, 50, 20]
```

### 힙에서 원소 삭제
`heappop` 함수는 가장 작은 원소를 힙에서 제거함과 동시에 그를 결괏값으로 리턴함

```python
result = heapq.heappop(heap)

print(result)
print(heap)

>> 10
>> [20, 50]
```

### 최대 힙 만들기
파이썬의 `heapq` 모듈은 **최소힙**으로 구현되어 있기 때문에 힙 구현을 위해서는 트릭이 필요함   
**y = -x 변환을 하면 최솟값 정렬이 최댓값 정렬로 바뀌는 원리**

힙에 원소를 추가할 때 `(-item, item)`의 튜플 형태로 넣어주면 튜플의 첫 번째 원소를 우선순위로 힙을 구성하게 된다.   

이때 원소 값의 부호를 바꿨기 때문에 최소 힙으로 구현된 `heapq` 모듈을 최대 힙 구현에 활용할 수 있다.

아래 예시는 `heap_items`에 있는 원소들을 `max_heap`이라는 최대 힙 자료구조로 만드는 코드 예시

```python
heap_items = [1, 3, 5, 7, 9]

max_heap = []
for item in heap_items:
    heapq.heappush(max_heap, (-item, item))

print(max_heap)

>> [(-9, 9), (-7, 7), (-3, 3), (-1, 1), (-5, 5)]
```

`heappush` 함수를 통해 `item`을 힙에 push 할 때 (-item, item)의 튜플 형태로 넣은 것을 확인할 수 있음

그 결과, `heappop`을 사용하게 되면 힙에 있는 **최댓값**이 반환되는 것을 확인할 수 있다. 이때 실제 원소 값은 튜플의 두 번째 자리에 저장되어 있으므로 `[1]` 인덱싱을 통해 접근하면 됨

```python
max_item = heapq.heappop(max_heap)[1]  # (-9, 9) 중 9를 추출
print(max_item)

>> 9
```

### [예제] 주어진 리스트의 모든 값이 T 이상이 될 때까지 최솟값 두 개를 합치기
N개의 비커에 액체가 담겨 있다. 모든 비커에 있는 액체의 양이 T 이상이 될 때까지 **액체가 가장 적게 담긴 두 비커의 액체를 합쳐**가려 한다. 각 비커에 담겨있는 액체의 양을 표기한 리스트 L과 기준 T가 주어질 때, 모든 비커의 양이 T 이상이 될 때까지 필요한 작업 횟수를 리턴하는 함수를 구현해보자. (합쳐지지 않을 경우 -1을 리턴)

```python 
T = 4
L = [1, 2, 3, 4, 5, 6, 7]

import heapq

def heap_example(L, T):
    heapq.heapify(L)  # 리스트를 힙 구조로 변환

    result = 0

    while len(L) >= 2:  # IndexError 방지
        min_ = heapq.heappop(L)  # 힙에서 최솟값을 가져옴

        # 최솟값이 T보다 크다면 더 이상 합쳐질게 없으니 -1을 리턴
        if min_ >= T:
            break

        else:
            min_2 = heapq.heappop(L)  # 두번째로 작은 값을 가져와 합친 값을 힙에 push
            heapq.heappush(L, min_ + min_2)
            result += 1  # 합친 횟수 +1

    # 합친 후 T보다 크면 합친횟수를 리턴, 그렇지 않으면 -1를 리턴
    if L[0] > T:
        return result
    else:
        return -1
```

```python
T = 4
L = [1, 2, 3, 4, 5, 6, 7]

step1 : [1, 2]를 합침
        -> [3, 3, 4, 5, 6, 7]

step2 : [3, 3]을 합침
        -> [6, 4, 5, 6, 7]

모든 비커의 액체 양이 4 이상이므로 STOP
```