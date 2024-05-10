# 05 String
## 1. CONCAT
여러 문자열을 하나의 문자열로 합치는 함수

여러 문자열 혹은 컬럼 값을 합쳐서 가져와야 하는 경우가 있다.   
이럴때 **CONCAT**함수를 사용한다.    
**CONCAT 함수는 둘 이상의 문자열을 입력한 순서대로 합쳐서 반환해주는 함수이다.**

### 사용법
```sql
CONCAT(문자열1, 문자열2, [, 문자열3 ...])
```

### 예제 쿼리(Example Query)
#### 기본 사용
##### 쿼리
```sql
SELECT CONCAT('안녕하세요.', '감사해요.', '잘있어요.', '다시만나요.') AS hello;
```
##### 결과
|hello|
|-|
|안녕하세요.감사해요.잘있어요.다시만나요.|

#### 컬럼 데이터 합치기
##### 예제 테이블 : hero_collection
|idx|type|name|
|-|-|-|
|1|1|안중근|
|2|1|윤봉길|
|3|2|김유신|
|4|2|이순신|
|5|3|이성계|
|6|3|왕건|
|7|4|반갑수|

##### 쿼리
```sql
SELECT CONCAT(type, '::', name) as hero_name FROM hero_collection;
```

##### 결과
|hero_name|
|-|
|1::안중근|
|1::윤봉길|
|2::김유신|
|2::이순신|
|3::이성계|
|3::왕건|
|4::반갑수|

## 2. SUBSTRING
문자열을 추출할 때 사용하는 함수

SUBSTRING은 거의 모든 언어나 DBMS에 자체적으로 내장 되어 있고, 사용방법도 비슷함

SUBSTR = SUBSTRING, 둘 다 사용 가능하며 완전 동일함

### 사용법
```sql
SUBSTR(STR, POS)
SUBSTR(STR FROM POS)
SUBSTR(STR, POS, LEN)
SIBSTR(STR FROM POS FOR LEN)
```

|STR|POS|LEN|
|-|-|-|
|원본 문자열|시작 위치값|가져올 길이값|

### 예제
**SUBSTR(STR, POS)**
```sql
SELECT SUBSTR('동해물과백두산이', 5);

>> 백두산이 (5번째 문자부터 start)
```

**SUBSTR(STR FROM POS)**
```SQL
SELECT SUBSTR('동해물과백두산이' FROM 5);

>> 백두산이 (5번째 문자부터 start)
```

**SUBSTR(STR, POS, LEN)**
```SQL
SELECT SUBSTR('동해물과백두산이', 3, 4);

>> 물과백두 (3번째 문자부터 4글자만 가져오기)
```

**SUBSTR(STR FROM POS FOR LEN)**
```SQL
SELECT SUBSTR('동해물과백두신이' FROM 3 FOR 4);

>> 물과백두 (3번째 문자부터 4글자만 가져오기)
```


#### POS 마이너스 사용
> POS는 음수로도 사용 가능하며 사용 시, 문자열 끝에서부터 체크한다.

**SUBSTR(STR, POS)**
```SQL
SELECT SUBSTR('동해물과백두산이', -4);

>> 백두산이 (뒤에서 4번째 문자부터 시작)
```

**SUBSTR(STR FROM POS)**
```SQL
SELECT SUBSTR('동해물과백두산이' FROM -4);

>> 백두산이 (뒤에서 4번째 문자부터 시작)
```

**SUBSTR(STR, POS, LEN)**
```SQL 
SELECT SUBSTR('동해물과백두산이', -6, 4);

>> 물과백두 (뒤에서 6번째 문자부터 4글자만 가져오기)
```

**SUBSTR(STR FROM POS FOR LEN)**
```SQL
SELECT SUBSTR('동해물과백두산이' FROM -6 FOR 4);

>> 물과백두 (뒤에서 6번째 문자부터 4글자만 가져오기)
```





