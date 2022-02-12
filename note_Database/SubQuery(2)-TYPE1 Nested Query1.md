## TYPE 1 NESTED QUERY = 한정자

#### "외부 테이블의 (row의) 한정자"

- If your subquery returns more than one row, it can be referred to as a **multiple-row subquery**. Note that this subquery type includes 
  - (1) subqueries that return one column with multiple rows (i.e. a list of values)
  - (2) subqueries that return multiple columns with multiple rows (i.e. tables).

---

- 사용 위치 :
  - WHERE
  - HAVING
- 특징 :
  - 한번만 실행된다
  - OUTER QUERY에 대한 참조 없다 -> independent nest query라고도 불린다
- 사용 시 특징
  - in 사용
  - **일반적인 in 사용 방법 : in ( , , )**
  - **nested query와 in 사용 방법 : in (select문)**
    - 즉, select문이 여러개의 값을 가져온다는 의미가 된다. in의 조건 여러개를 list 형태로 가져온다.



#### Example

```sql
# type1 nested query
# 외부와 상관없는 쿼리
# 단순히 외부 테이블의 row를 한정짓기 위한 조건 중 하나일 뿐이다.

select facno, faclastname, facdept
from faculty
where facdept = 'FIN'
and facno in 
(select facno 
from offering 
where courseno like 'is%');
```



```sql
select facno, faclastname, facdept
from faculty
where facdept = 'FIN' 
and facno in 
(select facno 
from offering 
where courseno like 'is%' and courseno in 
	(select courseno from course
    where CrsUnits = 4) );
```

