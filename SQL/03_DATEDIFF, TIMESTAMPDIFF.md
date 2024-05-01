# 03 DATEDIFF, TIMESTAMPDIFF 함수
MySQL에서 두 날짜간의 차이를 가져올 때 사용하는 함수

**DATEDIFF**   
단순히 `일` 차이를 가져올 때 사용하는 함수

**TIMESTAMPDIFF**   
차이를 `연, 분기, 월, 주, 일, 시, 분, 초`를 지정해 가져올 때 사용하는 함수

## 사용법
### DATEDIFF   
```sql
DATEDIFF(날짜1, 날짜2);
```
**날짜1 - 날짜2** 동작

### TIMESTAMPDIFF
```sql
TIMESTAMPDIFF(단위, 날짜1, 날짜2);
```

**단위**    
- SECOND : 초
- MINUTE : 분
- HOUR : 시
- DAY : 일
- WEEK : 주
- MONTH : 월
- QUARTER : 분기
- YEAR : 연

## 예제
### DATEDIFF
```sql
SELECT DATEDIFF('2018-03-28 23:59:59', '2017-03-01 00:00:00');

>> 392 -- (일 단위)
```

### TIMESTAMPDIFF : 초
```sql
SELECT TIMESTAMPDIFF(SECOND, '2017-03-01', '2018-03-28');

>> 33868800
```

### TIMESTAMPDIFF : 분
```sql
SELECT TIMESTAMPDIFF(MINUTE, '2017-03-01', '2018-03-28');

>> 564480
```

### TIMESTAMPDIFF : 시
```sql
SELECT TIMESTAMPDIFF(HOUR, '2017-03-01', '2018-03-28');

>> 9408
```

### TIMESTAMPDIFF : 일
```sql
SELECT TIMESTAMPDIFF(DAY, '2017-03-01', '2018-03-28');

>> 392
```

### TIMESTAMPDIFF : 주
```sql
SELECT TIMESTAMPDIFF(WEEK, '2017-03-01', '2018-03-28');

>> 56
```

### TIMESTAMPDIFF : 월
```sql
SELECT TIMESTAMPDIFF(MONTH, '2017-03-01', '2018-03-28');

>> 12
```

### TIMESTAMPDIFF : 분기
```sql
SELECT TIMESTAMPDIFF(QUARTER, '2017-03-01', '2018-03-28');

>> 4 
```

### TIMESTAMPDIFF : 연
```sql
SELECT TIMESTAMPDIFF(YEAR, '2017-03-01', '2018-03-28');

>> 1 
```