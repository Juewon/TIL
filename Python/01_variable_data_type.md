# Python 기초 

## 1. 개요
파이썬을 다시 공부하면서 새로 알게된 개념이나 다시 봐야 할 개념들을 중심으로 정리해보았다.

## 2. String interpolation (문자열 보간)
string interpolation (문자열 보간)이란 ?   

문자열 데이터에 값을 줄 수 있는 변수를 삽입하여, 데이터를 좀 더 동적으로 표현 할 수 있는 방법

- `%-formatting`
  - `%d` : 정수
  - `%f` : 실수
  - `%s` : 문자열

- `str.format()`
- `f-strings`

```python
name = '서주원'
score = 3.5
```

### 2.1 %-formatting
```python
print('내 이름은 %s, 성적은 %f' % (name, score))

=> 내 이름은 서주원, 성적은 3.500000
```

### 2.2 str.format()
```python
print('내 이름은 {}, 성적은 {}'. format(name, score))

=> 내 이름은 서주원, 성적은 3.5
```

### 2.3 f-string
```python
print(f'내 이름은 {name}, 성적은 {score}')

=> 내 이름은 서주원, 성적은 3.5
```

### 2.3.1 f-string 연산과 출력형식 지정
```python
pi = 3.141592
print(f'원주율은 {pi:.3}. 반지름이 2일 때ㅐ 원의 넓이는 {pi * 2 * 2}이다.')

=> 원주율은 3.14. 반지름이 2일 때 원의 넓이는 12.566367이다.
```
**\* {x:.3} - x의 소수점아래 3번째 자리에서 반올림하기.**