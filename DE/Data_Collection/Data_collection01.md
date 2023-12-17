# Web Browser 컨트롤
**Content**
- Webbrowser Module
- Web Communication Rules

## 1. Webbrowser Module
- 클라이언트에 해당하는 웹 브라우저를 **핸들링** 할 수 있는 모듈
- 매개변수 : **url**을 전달(접속하고자 하는 웹 사이트)
```python
import webbrowser  # webbrowser 모듈 import

url = 'www.naver.com'  # 핸들링 할 웹 브라우저 주소 저장

webbrowser.open(url)  # open 메서드를 활용해 저장된 url값을 전달

>> True  # 반환값이 True면 브라우저 실행 정상 완료
```
- 코드를 이용해 브라우저를 연결, 브라우저가 서버측으로 요청을 보내는것까지 담당해주는 코드

## 2. Web Communication Rules
- **URL의 구조**
    > URL = Domain + Parameter로 구성되어 있다.

- **Domain**
    >  `?` 기호를 통해 Domain과 Parameter를 구분할 수 있다.
  - https://search.naver.com/search.naver?where=nexearch&sm=top_hty&fbm=0&ie=utf8&query=python
  - Domain section : https://search.naver.com/search.naver
  - Parameter section : where=nexearch&sm=top_hty&fbm=0&ie=utf8&query=python

- **Parameter**
  - URL Parameter 란?
    - 사이트의 문서를 요청할 때 서버로 전달되는 정보
  - `Parameter = value`의 형태로 구성
  - 네이버 사이트에서 python을 검색했을 때, **query`=`python** 이라는 파라미터 값을 이용해 검색하게 됨
  - 파라미터 사이의 구분은 `&` 기호를 통해 구분한다.
  - where=nexearch`&`sm=top_hty`&`fbm=0&ie=utf8`&`query=python

> 파라미터는 url마다 다르며, 대부분의 url은 이러한 통신 규칙들을 통해 구성된다.