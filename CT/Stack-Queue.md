# 스택(Stack) / 큐(Queue)
## 스택(Stack)
> 한쪽 끝에서만 넣고/빼는 구조 → **LIFO**(Last-In First-Out, 나중에 넣은게 먼저 나옴)

- **주요 연산**: `push`(넣기), `pop`(빼기), `peek`(맨 위 보기)
- **예시/비유**: 접시 더미, 되돌리기(Undo)
- **파이썬**: `list`로 `append`/`pop()`
    ```python
    stack = []
    stack.append(1)
    stack.append(2)
    top = stack.pop()  # 2
    ```
- **쓰임새**: 괄호 검사, DFS, 백트래킹, 최근 상태 저장

## 큐(Queue)
> 앞에서 빼고 뒤에서 넣는 구조 → **FIFO**(First-In First-Out, 먼저 넣은게 먼저 나옴)

- **주요 연산**: `enqueue`(넣기), `dequeue`(빼기)
- **예시/비유**: 줄 서기, 작업 대기열
- **파이썬**: `collections.deque` 

```python
from collections import deque
q = deque()
q.append(1)
q.append(2)
x = q.popleft(1)
```
- **쓰임새**: BFS, 생산자-소비자, 작업 스케줄링, 윈도우 처리

**한줄 요약**
>**스택=LIFO(접시 더미)**, **큐=FIFO(줄 서기)** - DFS/괄호검사엔 스택, BFS/작업처리는 큐

## 문제 풀이
### [프로그래머스] 기능개발
>배포마다 몇 개 기능이 함께 나가는지 구하는 문제

**풀이**    
1. 각 작업이 완료되기까지 걸리는 **일수** 구하기
   `days[i] = ceil((100 - progress[i] / speed[i]))`

2. **앞선 작업이 기준**이 되어, 그 기준 일수 이하로 끝나는 뒤 작업들은 **같이 배포**하고, 더 큰 일수가 나오면 새 배치를 시작

```python
import math  # math.ceil: 올림(ceiling) 연산을 위해 사용

def solution(progresses, speeds):
    # 각 작업이 완료되기까지 걸리는 '일수'를 계산
    # 남은 작업량(100 - p)을 하루 속도 s로 나누고, 올림 처리(소수점이 나오면 다음날 배포)
    days = [math.ceil((100 - p) / s) for p, s in zip(progresses, speeds)]
    # 예) progresses=[90, 30, 55], speeds=[1, 30, 5] → days=[7, 3, 9]

    answer = []  # 배포마다 몇 개가 같이 나가는지 기록할 리스트
    cur = days[0]  # 가장 앞 작업의 완료일
    cnt = 1  # 현재 배치에 들어간 작업 개수

    # 두번째 작업부터 순회하며 묶을 수 있는지 확인
    for d in days[1:]:
        if d <= cur:
            # 현재 기준일(cur) 안에 끝나는 작업이면 같은 날 배포 → 같은 묶음에 추가
            cnt += 1
        else:
            # 기준일보다 늦게 끝나는 작업이면 새 배치 시작
            answer.append(cnt)  # 이전 배치 개수 확정
            cur = d  # 새 배치 기준 갱신
            cnt = 1  # 새 배치 카운트 리셋
    
    answer.append(cnt)  # 마지막 배치 개수 반영
    return answer
```