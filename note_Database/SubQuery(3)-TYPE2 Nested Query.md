## TYPE 2 NESTED QUERY

- 특징
  - NESTED LOOP와 비슷
  - 외부 쿼리의 each row마다 한번씩 실행된다 - 외부에 참조가 있다
- 사용 시 특징
  - exists를 사용
    - The EXISTS operator checks if the row FROM the subquery matches any row in the outer query. If there’s no data matched, the EXISTS operator returns FALSE.
    - 즉, **"서브쿼리의 결과가 존재하는지"** 만 판단하는 것이다!!!
  - FROM / WHERE 을 사용하는 join과 매우 흡사.
    - 같은 점 : pk = fk 일치시키기
    - 다른 점 : TYPE 2 NESTED QUERY는, from에 테이블 하나만 적는 것

---

```sql
# type2 nested query
# 서브쿼리의 select 다음에 아무거나 상관 없다(*던지, 어떤 컬럼이던지 상관없음)

select facno, faclastname, facdept
from faculty
where facdept = 'MS' 
and not exists 
(select *
from offering 
where offterm = 'winter' 
and faculty.facno = offering.facno); # join 역할을 해서, 첫 결과 각각의 row에 대해 조건을 맞춰볼 수 있도록 한다
```

