### JPQL 소개

1. em.createQuery( jpql, 반환할 엔티티의 클래스 타입 )
   - 실행할 jpql
   - 반환할 엔티티의 클래스 타입(Member.class) 넘기기
2. getResultList()
   - JPQL을 SQL로 변환해서, 데이터베이스를 조회한다.



### QueryDSL 소개

- (어노테이션 프로세서를 사용하여) 쿼리 전용 클래스를 만들어야 한다



### 네이티브 SQL 소개

1. em.createNativeQuery( sql, 반환할 엔티티의 클래스 타입)
2. getResultList()



### jdbc 직접 사용, 마이바티스 같은 sql 매퍼 프레임워크 사용

- JPA를 우회하여 데이터베이스에 접근하는 것
- 문제 : 영속성컨텍스트와 데이터베이스가 일치하지 않을 수 있는 문제가 생긴다.
- 해결책 : JPA 우회하여 SQL을 실행하기 전, 영속성 컨텍스트를 수동으로 flush() 해주기 -> DB와 영속성 컨텍스트 동기화









---

## JPQL 기본 문법

- https://data-make.tistory.com/614

- 반드시 별칭 사용해야 함. AS는 생략 가능



### 기본 예시





### 1. Query 객체 생성하기

- TypeQuery : 반환할 타입을 명확하게 지정할 수 있을 경우
  - em.createQuery( jpql, 엔티티.class)

- Query : 반환 타입을 명확하게 지정할 수 없을 경우

  - 즉, 여러 엔티티나 컬럼을 선택할 경우(반환 타입이 명확하지 않을 경우) 사용
  - em.createQuery( jpql )

### 2. 결과 조회

- query.getResultList() : 결과를 예제로 반환
  - 결과가 없을 경우 빈 컬렉션 반환

- query.getSingleResult() : 결과가 정확히 하나일 때 사용

  - 결과가 없으면 javax.persistence.NoResultException 예외 발생

  - 결과가 1보다 많으면 javax.persistence.NonUniqueResultException 예외 발생

