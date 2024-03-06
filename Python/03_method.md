# 03_Method
> 코딩테스트를 준비하면서 헷갈렸던 메서드들을 정리

Contents
- [03\_Method](#03_method)
  - [1. strip](#1-strip)
  - [2. 대/소문자 변환 메서드](#2-대소문자-변환-메서드)

## 1. strip
- `strip()`
  - 문자열의 시작과 끝에서 공백을 제거한 후 반환
  - `()` 안에 특정 값을 넣을 경우, 해당하는 문자열을 제거할 수 있음
  - 양쪽 제거
  ```python
  # 공백 제거
  string = "    abcde   "
  string.strip()

  >>> 'abcde'

  # 특정 문자열 제거
  string = "    abcde   "
  string.strip('c')

  >>> 'abde'
  ```
- `lstrip()`
  - 왼쪽 기준 공백, 원하는 문자열 제거
  ```python
  # 공백 제거
  string = "    abcde   "
  string.lstrip()

  >>> 'abcde    '

  # 특정 문자열 제거
  string = "    oooabcdeooo   "
  string.lstrip('o')

  >>> 'abcdeooo'
  ```
- `rstrip()`
  - 오른쪽 기준 공백, 원하는 문자열 제거
  ```python
  # 공백 제거
  string = "    abcde   "
  string.rstrip()

  >>> '    abcde'

  # 특정 문자열 제거
  string = "    oooabcdeooo    "
  string.rstrip('o') 

  >>> 'oooabcde'   
  ```
  
## 2. 대/소문자 변환 메서드
- `upper()` : 문자열을 대문자로 변환하기
  ```python
  str = 'apple'
  str = str.upper()
  print(str)

  >>> APPLE
  ```
- `lower()` : 문자열을 소문자로 변환하기
  ```python
  str = 'APPLE'
  str = str.lower()
  print(str)

  >>> apple
  ```
- `capitalize()` : 문자열의 첫 글자는 대문자로 나머지는 소문자로 변환하기
  ```python
  str = 'APPLE'
  str = str.capitalize()
  print(str)

  >>> Apple
  ``` 
- `title()` : 문자열의 각 단어의 첫글자를 대문자로 변환하기
  ```python
  str = 'APPLE BANANA CHERRY DURIAN'
  str = str.title()
  print(str)

  >>> Apple Banana Cherry Durian
  ```
- `swapcase()` : 문자열에 있는 모든 문자의 대/소문자를 반대로 변환하기
  ```python
  str = 'aPlLe BaNAnA CHeRrY DUrIaN'
  str = str.swapcase()
  print(str)

  >>> ApLlE bAnaNa chErRy duRiAn
  ```
- `isupper() / islower()` : 문자가 대/소문자인지 확인하는 함수
  - 함수 형태 : `string.isupper() / string.islower()`
  - 반환형 : Bool(True, False)
  - `isupper()`
    - 문자열이 모두 대문자인 경우에만 True를 반환
    - 오직 '알파벳 대문자'인 경우에만 True를 반환, 그렇지 않은 경우 False를 반환
    - ex) 공백, 한글, 알파벳 소문자, 기호 등이 있는 경우 False를 반환
  - `islower()`
    - 문자열이 모두 소문자인 경우에만 True를 반환
    - 오직 '알파벳 소문자'인 경우에만 True를 반환, 그렇지 않은 경우 False를 반환
    - ex) 공백, 한글, 알파벳 대문자, 기호 등이 있는 경우 False를 반환