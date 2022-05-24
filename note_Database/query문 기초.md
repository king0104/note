#### 쿼리문법 적용 순서

1. from

2. where

3. group by

4. having

5. order by

6. select



#### null 관련 이슈

- null은 값으로 이용되지 않는다
- null에서는 비교자 사용할 수 없음. 그래서 **is null / is not null** 으로만 null을 판단할 수 있다



#### 팁

- table은(select문의 결과는), 결국 row들의 집합이다 (특정 컬럼만을 선택해서 표현하는 row의 집합.)

