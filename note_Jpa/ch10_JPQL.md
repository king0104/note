## JPQL

#### sql 코드 작성 꿀팁

- **조건을 적용할 테이블을, from 절**에 쓰자

  - ex)  xx세 이상의 회원 중 ..  ->  from member

  

---

#### JPQL 특징

- em.find()나 JPQL을 사용해서 조회한 엔티티도 영속성 컨텍스트가 관리하는 영속상태이다.(p.94)









#### JPQL 코드 작성법

```java
/* Example 2 */
// TODO: xx세 이상의 회원 중 파라미터로 받은 이름의 일부와 매칭되는 회원이 소속된 모든 팀
public List<Team> getTeamByMembersFirstNameAndAgeGreater(Integer age, String name) {
    EntityManager em = emf.createEntityManager();
    TypedQuery<Team> query = em.createQuery("select distinct m.team from Member m where " +
            "m.age >= :age and  m.username like concat('%',:name,'%')", Team.class);
    query.setParameter("age", age);
    query.setParameter("name", name);

    return query.getResultList();
}
```

