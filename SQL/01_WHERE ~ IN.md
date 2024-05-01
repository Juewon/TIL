# 01 WHERE ~ IN
**WHERE과 HAVING의 차이점**   
`WHERE`은 기본적으로 조건절로서 **우선적으로 모든 필드를 조건에 둘 수 있다.**   
하지만 having은 group by이 된 이후 특정한 필드로 **그룹화 되어진 새로운 테이블에 조건을 줄 수 있다.**

즉, 전체 테이블 자체에서 쿼리를 수행하고 싶다면 `where`    
전체 테이블을 그룹화 한 뒤, 해당 그룹에서 어떠한 조건을 걸어 가져오고 싶다면 `having`을 사용함

## WHERE절의 IN 사용법
1. WHERE **일치하길 원하는 컬럼명** IN (조건1, 조건2, 조건3 ...)   
   WHERE 뒤에 써준 컬럼과 IN 뒤로 나열한 조건들 중 일치하는 **ROW**를 가져오게 된다.   
   여기서 나열한 조건들은 **OR조건**으로 검색하게 된다.

2. WHERE **일치하지 않길 원하는 컬럼명** NOT IN (조건1, 조건2, 조건3 ...)    
   WHERE 다음에 써주는 컬럼명이 **일치하지 않길 원하는 컬럼명**인 **ROW**를 가져오게 된다.   
   위와 같이 **OR조건**이고, 해당되는 내용을 가져오지 않는다는 차이점이 있다.

### WHERE절의 IN 예시
```sql
SELECT FOOD_TYPE, REST_ID, REST_NAME, FAVORITES
FROM REST_INFO
WHERE (FOOD_TYPE, FAVORITES) IN (    
    SELECT FOOD_TYPE, MAX(FAVORITES) 
    FROM REST_INFO
    GROUP BY FOOD_TYPE 
)
ORDER BY 1 DESC;

-- WHERE ~ IN + 서브쿼리 구문을 써서 FOOD_TYPE별 최대 좋아요 수를 가진 FOOD_TYPE과, 좋아요수를
-- 포함하고 있는 ROW를 불러와 SELECT절대로 출력함
```