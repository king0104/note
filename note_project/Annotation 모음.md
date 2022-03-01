

### JPA

#### @GeneratedValue(strategy = GenerationType.xxx)
- @GeneratedValue(strategy = GenerationType.AUTO)
- **즉, id 값을 null로 하면 DB가 알아서 AUTO_INCREMENT 해준다.**

- https://gmlwjd9405.github.io/2019/08/12/primary-key-mapping.html

- db의 table을 만들 때, 해당 어노테이션을 적용한 필드와 매핑되는 필드에(99퍼센트 pk 필드) auto_increment를 해주어야 한다
- 그냥 간단하게, db의 pk필드를 auto_increment로 설정해주어야한다.

---

#### Entity와 Table을 매핑하는 어노테이션들

#### @Entity

- jpa가 관리하는 엔티티로 사용하겠다는 뜻

#### @Table

- jpa가 관리하는 엔티티를, 어떤 db의 테이블과 매핑할 지 정하는 것.
- name 속성 생략 시, 엔티티 이름을 테이블 이름으로 사용

#### @Id

- 엔티티의 필드 중 하나를, pk로 지정한다.

#### @Column

- 엔티티의 필드를, 테이블의 필드와 매핑



## Spring Security 관련

- @EnableWebSecurity : 스프링 빈으로 인식되도록 함
