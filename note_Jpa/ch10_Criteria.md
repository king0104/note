## Criteria

```java
/* Example 8 */
// TODO: 특정 팀의 xx세 이상 회원의 이름, 나이만 MemberDTO로 조회하여 리턴(나이 내림차순으로 정렬할 것)
public List<MemberDTO> getMembersByAgeGreaterAndEquals(Integer age) {
    EntityManager em = emf.createEntityManager();
    CriteriaBuilder cb = em.getCriteriaBuilder();

    // 1. 쿼리 + 반환타입 생성
    CriteriaQuery<MemberDTO> cq = cb.createQuery(MemberDTO.class);

    // 2. from절은 미리 만들어두기 ->  그래야 작업을 할 수 있음!!!!!!!!
    Root<Member> m = cq.from(Member.class);

    // 3. 조건 만들기
    Predicate predicate = cb.greaterThanOrEqualTo(m.get("age"),age);

    // 4. 쿼리 만들기
    // 4-1. cb로 클래스 만들 수 있다.
    cq.select(cb.construct(MemberDTO.class, m.get("username"), m.get("age")))
            .where(predicate)
            .orderBy(cb.desc(m.get("age")));

    // 4-1. 쿼리 실행
    return em.createQuery(cq).getResultList();

}

/* Example 9 */
// TODO: 특정 팀의 xx세 이상 회원의 이름, 나이만을 Tuple방식으로 조회하여, new MemberDTO로 리턴 (= same example 8)
public List<MemberDTO> getMembersByAgeGreaterAndEqualsByTuple(Integer age) {
    EntityManager em = emf.createEntityManager();


    CriteriaBuilder cb = em.getCriteriaBuilder();

    // 1. 쿼리 + 반환타입 생성
    CriteriaQuery<Tuple> cq = cb.createQuery(Tuple.class);

    // 2. from절은 미리 만들어두기 ->  그래야 작업을 할 수 있음!!!!!!!!
    Root<Member> m = cq.from(Member.class);

    // 3. 조건 만들기
    Predicate predicate = cb.greaterThanOrEqualTo(m.get("age"),age);

    // 4. 쿼리 만들기
    cq.multiselect(
                    m.get("username").alias("username"), // 별칭으로 저장
                    m.get("age").alias("age")
            ).where(predicate)
            .orderBy(cb.desc(m.get("age")));

    return em.createQuery(cq)
            .getResultList()
            .stream()
            .map(t->new MemberDTO(t.get("username",String.class),
                    t.get("age",Integer.class)))
            .collect(Collectors.toList());




}
```