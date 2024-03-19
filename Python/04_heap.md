# 힙 자료구조
https://littlefoxdiary.tistory.com/3   

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