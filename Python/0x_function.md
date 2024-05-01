# 함수
특정한 기능(function)을 하는 코드의 묶음

## 함수를 쓰는 이유
- 가독성
- 재사용성
- 유지보수성

<center>
    <img src="https://user-images.githubusercontent.com/18046097/61181741-2984fd80-a665-11e9-93b8-578c56689d0e.png", alt="programming principle">
</center>
: 코드가 많으면 많을수록 오류가 많이난다.

## 함수 선언과 호출
- `def` 키워드를 활용해 함수를 선언
- 함수는 동작후에 `return`을 통해 결과값을 전달
  - 반드시 하나의 객체를 반환한다.(`return`값이 없으면, `None`을 반환)
- `함수명()` 로 함수 호출
  - ex) `func()` / `func(val1, val2)`

### 활용법
```python
def <함수이름>(parameter1, parameter2):
    <코드 블럭>
    return value
```

<center>
    <img src="https://user-images.githubusercontent.com/18046097/61181742-2984fd80-a665-11e9-9d5c-c90e8c64953e.png", alt="function descrpition">
</center>   

- 함수 이름 및 변수명 또한 **예약어 / 내장함수 이름으로 사용하지 않는다.**