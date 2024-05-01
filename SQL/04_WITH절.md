# 04 WITH 절
`WITH`절은 서브쿼리를 만들고 재사용 가능한 **공통 테이블 표현식(Common Table Expression, CTE)**을 정의하는 방법이다.    
`WITH`절을 사용해 쿼리를 단순화하고 가독성을 높일 수 있다.

## WITH절 기본 구문
다음은 `WITH`절을 사용하는 기본적인 구문이다.
```sql
WITH [cte_name] AS (
    SELECT [column_name(s)]
    FROM [table_name]
    WHERE [condition]
)

SELECT [column_name(s)]
FROM [table_name]
JOIN [cte_name] ON [join_condition]
WHERE [condition];
```

`cte_name`은 임의 이름, 서브쿼리에서 반환된 결과를 참조할 수 있는 임시 테이블의 이름이다.

서브쿼리 내에서 SELECT문을 사용해 데이터를 검색하고 해당 결과 집합을 `cte_name`으로 정의한 CTE에 저장함    
그 후, CTE를 메인 쿼리에서 참조해 추가 데이터를 가져올 수 있다.

**실제 예제**    
부서 이름이 'Sales'인 모든 직원의 이름, 직책 및 급여 정보를 가져오기 위해 쿼리를 작성   
```sql
WITH SalesEmployees AS (
    SELECT FirstName, LastName, JobTitle, Salary
    FROM employees e
    JOIN departments d ON e.DepartmentID = d.DepartmentID
    WHERE DepartmentName = 'Sales'
)
SELECT FirstName, LastName, JobTitle, Salary
FROM SalesEmployees;
```

위 예제에서 부서 이름이 'Sales'인 모든 직원의 이름, 직책 및 급여 정보를 가져오기 위해, `SalesEmployees`라는 CTE를 정의함.   
이후 `SalesEmployees` CTE를 메인 쿼리에서 참조해 결과를 가져올 수 있다.

이와 같이 `WITH`절을 사용하면, 하나 이상의 서브쿼리에서 반환된 데이터를 단일 쿼리에서 재사용할 수 있다.    
**이는 코드 중복을 줄이고 쿼리의 가독성을 향상시키는데 도움이 된다.**