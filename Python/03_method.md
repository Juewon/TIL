# 03_Method
> 코딩테스트를 준비하면서 헷갈렸던 메서드들을 정리

Contents
- [03\_Method](#03_method)
  - [1. strip](#1-strip)

## 1. strip
- strip()
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
- lstrip()
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
- rstrip()
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
  
