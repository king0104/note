#### @ManyToOne, @OneToMany

- 정의 : 연관관계를 매핑한다
- 쉽게 생각하기 : **엔티티 클래스의 필드로, 엔티티 클래스를 가질 수 있다. 즉, 어플리케이션 레벨에서 참조가 가능하게 된다!!!**
  - app level에서 fk를 쓰지 않고도 직접 참조가 가능하니까, 코드 사용이 훨씬 편하다



#### @JoinColumn(name = "db의 column name")

- 외래키 매핑할 때 사용한다

- 자바 코드 측 엔티티 필드를, 디비 측 컬럼에 매핑하기 위해 사용하는 것. 

  

#### @Column

- 컬럼