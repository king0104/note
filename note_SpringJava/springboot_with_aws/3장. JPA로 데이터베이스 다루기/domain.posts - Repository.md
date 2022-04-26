### PostsRepository

- JpaRepository를 사용한다

- ```java
  public interface PostRepository extends JpaRepository<Posts, Long> {
  
  }
  ```



- @Repository를 추가할 필요가 없다!!!!

  - JpaRepository 상속받으면 자동으로 빈으로 등록된다

  

- **주의점 : Entity 클래스와 기본 Entity Repository는 함께 위치해야 한다.** 
  왜냐하면, Entity 클래스는 기본 Entity Repository없이 제대로 역할을 할 수가 없기 때문이다.

  - 그렇기 때문에, 도메인 패키지에서 이 둘을 함께 관리하는 것이다.