- https://data-make.tistory.com/614



- 반드시 별칭 사용해야 함. AS는 생략 가능

### 기본 예시





### Query 객체 생성하기

- TypeQuery : 반환할 타입을 명확하게 지정할 수 있을 경우

- Query : 반환 타입을 명확하게 지정할 수 없을 경우

  ,여러 엔티티나 컬럼을 선택할 경우(반환 타입이 명확하지 않을 경우) 사용

### 결과 조회

- query.getResultList() : 결과를 예제로 반환
  - 결과가 없을 경우 빈 컬렉션 반환

- query.getSingleResult() : 결과가 정확히 하나일 때 사용

  - 결과가 없으면 javax.persistence.NoResultException 예외 발생

  - 결과가 1보다 많으면 javax.persistence.NonUniqueResultException 예외 발생

