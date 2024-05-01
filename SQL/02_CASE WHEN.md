# 02 CASE WHEN 구문
SQL에서 매우 자주 쓰이는 구문  

CASE WHEN 구문은 **SELECT절에 쓰임**

## 표현식 : CASE WHEN THEN
**사용 형식**
```SQL
CASE WHEN 조건1 THEN 값1
     WHEN 조건2 THEN 값2
                .
                .
     ELSE 값n
END
```

1. 새로운 열을 생성하는 경우
```sql
SELECT CASE WHEN 기존 열 = 조건1 THEN '값 1'
            WHEN 기존열 = 조건2 THEN '값 2'

            ...

            (ELSE '값 N') END AS 새로운 열
```

2. 열을 집계하는 경우 (집계함수와 함께 사용) : 집계 열에 집계함수를 적용
```sql
SELECT 집계함수((DISTINCT) CASE WHEN 기존 열 = 조건 THEN 집계 열 (ELSE 값) END)
        AS 새로운 열
```

### 예제.
#### 1. 새로운 열 생성 : 고객 세그먼트 나누기   
Q. ageband열의 age값이 20~30이면 '2030', 40~50이면 '4050', 나머지는 'other'의 값을 갖는 **새로운 열 [ageband_seg]** 를 만드시오 

**CASE WHEN을 사용하게 되면 기존에 있는 열의 조건에 따른 새로운 값을 갖는 새로운 열이 만들어지게 된다.**

```sql
SELECT *,
        CASE WHEN ageband BETWEEN 20 AND 30 THEN '2030'
        WHEN ageband BETWEEN 40 AND 50 THEN '4050'
        ELSE 'other' END AS ageband_seg
FROM MEMBER
```

##### ELSE를 쓰지 않는 경우
ELSE는 꼭 쓸 필요 없이 생략 가능하다. **ELSE를 빼고 쓰면 전부 NULL처리가 된다**
```sql
-- NOT USING 'ELSE' -> it becomes 'NULL'
SELECT *,
        CASE WHEN ageband BETWEEN 20 AND 30 THEN '2030'
        WHEN ageband BETWEEN 40 AND 50 THEN '4050'
        END AS ageband_seg
FROM MEMBER
```

#### 2. 열 집계 : 연도별 회원 수 계산
CASE WHEN의 두번째 쓰임새는 열을 집계하는 용도로도 쓰인다.   
예를 들어, 위의 MEMBER 테이블에서 가입일자가 2018년과 2019년도에 가입한 멤버 수를 성별과 나이대로 그룹화해 출력해보자면,

```sql
SELECT gender, ageband,
        COUNT(CASE WHEN YEAR(join_date) = 2018 THEN mem_no END) AS join_18,
        COUNT(CASE WHEN YEAR(join_date) = 2019 THEN mem_no END) AS join_19
FROM MEMBER
GROUP BY gender, ageband
ORDER BY 1
```

## 조건식 : CASE WHEN (IN, ANY, EXISTS ...)
- 하나 이상의 표현식과 관계 연산자(논리 연산자)가 결합된 식
- 연산자는 논리연산자, 관계연산자, 기타연산자(**IN, ANY, SOME, ALL, EXISTS, LIKE, BETWEEN**)
  - **LIKE는 될 수 있으면 안 쓴다.**

## IN 연산자
- 주어진 값 중 비교항목이 포함되면 TRUE를 반환하는 연산자
- SOME, ANY와 같은 기능
- OR 연산자로 대치 가능 => **OR 연산자보다 단순 간단**
