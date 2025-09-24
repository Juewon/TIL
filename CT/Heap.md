# 힙(Heap)
Heap은 **완전 이진트리**의 한 종류로써, **우선순위 큐**(Priority Queue)를 위해 고안된 자료 구조이다. 특히, 다수의 자료에서 **최소값**과 **최대값**을 **빠르게 찾을 수 있는 특징**을 갖고 있음

<figure style="text-align:center;">
  <img src="https://github.com/user-attachments/assets/952f9620-4d3b-4ed9-b8e7-ba04fbb6dcc8"
       alt="Image" width="400" height="200" />
  <figcaption>Heap</figcaption>
</figure>

## Heap의 종류
- 최대 힙(Max Heap)
  - 부모 노드의 값이 자식 노드 보다 크거나 같은 경우를 만족하는 완전 이진 트리
  - 부모 노드의 값이 항상 자식 노드보다 크거나 같기 때문에, Root Node는 항상 **최대값**을 가지게 된다

- 최소 힙(Min Heap)
  - 부모 노드의 값이 자식 노드보다 작거나 같은 경우를 만족하는 완전 이진 트리
    - key(parents node) <= key(child node)
  - 부모 노드의 값이 항상 자식 노드보다 작거나 같기 때문에 Root Node는 항상 **최소값**을 가지게 된다

## 문제 풀이
### [프로그래머스] 더 맵게
**문제 요약**
- 모든 음식의 스코빌 지수를 **K 이상**으로 만들때 사용되는 횟수 구하기
- 규칙: 가장 작은 두 음식 `a`, `b`를 꺼내 **새 음식 = a + 2*b**로 섞어 다시 넣는다
- 이 과정을 반복해 전부 `>=K`가 되면 **섞은 횟수**를 반환, 불가능하면 **-1**

[문제 링크](https://school.programmers.co.kr/learn/courses/30/lessons/42626)

**해결 방법**   
**그리디 + Min-Heap 방법 사용**
- 매번 **가장 작은 두 개**를 꺼내야 하므로 **min-heap**을 사용해 정렬 후, `pop`/`push` 사용해 요구사항 달성
- 초기 배열을 `heapify`(O(n)) 후, 조건을 만족할 때까지 반복

**알고리즘**    
1. `(scoville)`을 `heapify` 시키기 (heapq 라이브러리 사용)
2. **가장 작은 값이 이미 K 이상**이면 0 반환
3. 아니라면 while:
   - 힙에 원소가 2개 미만이면 불가능 → -1
   - `a=heappop()`, `b=heappop()`, `mix=a+2*b` 계산 후 `heappush(mix)` 하고 카운트 + 1
   - Root(최솟값)가 **K 이상**이면 종료

- `heapq.heappop(arr)` → arr 내 가장 작은 원소 빼기, 제자리 변환
- `heapq.heappush(arr, value)` → arr로 value push, 크기 순서대로 자동 배치

**체크포인트**    
- 첫번째 원소가 K값과 같거나 크면 0 return
- 원소가 1개 남아있는데도 `<K`이면 -1 return

```python
import heapq  # Heap 라이브러리

def solution(scoville, K):
    heapq.heapify(scoville)             # 원소들을 오름차순으로 바로 정렬

    if scoville[0] >= K:                # 첫번째 원소가 K보다 크면 섞을 필요 없음. 바로 return
        return 0

    # 규칙에 맞춰 섞는 로직
    cnt = 0
    while len(scoville) >= 2:               # 두 개 음식 남을때까지 반복. 하나 남을 경우 어차피 return 
        a = heapq.heappop(scoville)         # heapq.heappop으로 가장 작은 
        
        # 첫번째 원소 pop
        if a >= K:
            return cnt                      # a가 K보다 클 경우, cnt 반환
        
        b = heapq.heappop(scoville)         # 두번째로 작은 원소 pop
        mix_food = a + b*2                  # 규칙대로 음식 섞기
        heapq.heappush(scoville, mix_food)  # 섞은 후 heapq.heappush로 밀어 넣기 (자동 정렬)
        cnt += 1                            # 섞은 횟수 추가

        if scoville[0] >= K:                # 마지막 하나 남을 경우 종료
            return cnt
    
    return -1                               # 마지막까지 K 이상으로 섞이지 않으면 -1 출력
```



