## SUBQUERY

### SUBQUERY

- 하나의 SQL안에 포함된 또 다른 SQL문
- 괄호 없음 : MAIN QUERY
  - 서브쿼리 컬럼 사용 불가능
- 괄호 있음 : SUBQUERY
  - 메인쿼리 컬럼 사용 가능

---

### 사용 유형

**SELECT 스칼라 서브쿼리**

**FROM 인라인 뷰**

**WHERE 중첩 서브쿼리**

---

### 종류

#### Scalar Subquery

- SELECT 문에 나타남

#### Inine View

- FROM 문에 나타남

#### Nested Subquery

- WHERE 문에 나타나는 서브쿼리
  1. 단일 행
  2. 복수 행
  3. 다중 컬림

---

- 서브쿼리 실행 후 -> 메인 쿼리 실행

### 조건

- 서브쿼리는 **SELECT문**으로만 작성 할 수 있다. (**SELECT**문 쿼리밖에 사용 할 수 없는것 이다. **SELECT**문에만 사용 하는 것이 아니라)
- 반드시 괄호()안에 존재하여야 한다.

- 괄호가 끝나고 끝에 ;(세미콜론)을 쓰지 않는다.

- ORDER BY를 사용 할 수 없다.

---



## 1. Scalar subquery

- return **single value**

  - 즉, 하나의 row이고 하나의 col 인 것만 리턴
  - 즉, 어떤 하나의 값일 뿐이다!!!
    - ex) AVG(col), SUM(col) 등등

- 종류1

  - MAX(), MIN()

    - ```sql
      SELECT MAX(column_name) FROM table_name;
      ```

    - 선택된 칼럼의 가장 큰 값(작은 값)을 가져온다

  - COUNT()

    - ```sql
      SELECT COUNT(column_name) FROM table_name;
      ```

    - row의 갯수를 계산해준다

    - 주로, count(*) 로 사용한다

  - DISTINCT

    - ```sql
      select distinct column_name from table_name;
      ```

      

    - 중복 제거 **키워드(함수 아님)**

    - 선택된 칼럼의 중복되는 값을 제거한 결과를 반환한다

- 종류2

  - ```sql
    SELECT (@hour := @hour + 1) AS HOUR,
    (select count(*) FROM animal_outs where hour(datetime) = @hour) AS COUNT
    from animal_outs
    where @hour < 23
    ```

    


## 2. Nested subquery

### 종류

1. return  one col & mutiple rows
   - list of values
2. return mutiple col & mutiple rows
   - table

---

---



SubQuery(2)-TYPE1 Nested Query1과 SubQuery(3)-TYPE2 Nested Query1 에서 자세히 알아보자!