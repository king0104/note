- manytoone 어디다가 사용하지?
- 엔티티매니저는 어디서 사용하지?
  - save를 db가 아니라 엔티티매니저에 저장하는 것으로 한다.

- JpaRepository vs Entity Manager 둘 중 하나 골라서 사용하면 된다.
  - jpaRepo : 직접 db에 저장
  - em : 영속성 컨텍스트에 저장 (jpa가 알아서 db에 저장해줌)