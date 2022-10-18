### 트랜잭션

- **데이터베이스의 상태를 변경**하는 작업 또는 **한번에 수행되어야 하는 연산들**을 의미한다.
- **begin, commit** 을 자동으로 수행해준다.
- 예외 발생 시 **rollback** 처리를 자동으로 수행해준다.
- 트랜잭션은 4가지의 성질을 가지고 있다.



#### 트랜잭션 4가지 성질

원자성(Atomicity)

> 한 트랜잭션 내에서 실행한 작업들은 하나의 단위로 처리한다. 즉, 모두 성공 또는 모두 실패.

일관성(Consistency)

> 트랜잭션은 일관성 있는 데이타베이스 상태를 유지한다. (data integrity 만족 등.)

격리성(Isolation)

> 동시에 실행되는 트랜잭션들이 서로 영향을 미치지 않도록 격리해야한다.

영속성(Durability)

> 트랜잭션을 성공적으로 마치면 결과가 항상 저장되어야 한다.



#### @Transactional

- 데이터베이스의 상태를 변경하는 메서드에 붙여준다

- 예를 들어, 

  - ```java
    @Transactional
        public Long save(PostsSaveRequestDto requestDto) {
            return postsRepository.save(requestDto.toEntity()).getId();
        }
    ```

  - 위와 같이 **메서드가 DB에 접근하게 되는 메서드라면, @Transactional을 사용하는 것이다**

  - 따라서, **Service 레이어에 사용되는 메서드는 웬만해서는 @Transactional을 붙인다**고 생각하면 된다.



#### @Transactional(readOnly = true)

- 트랜잭션 범위는 유지하되, **조회 기능**만 남겨두는 것.
- 조회 속도를 개선할 수 있다
- 등록, 수정, 삭제 기능이 전혀 없는, only 조회만 하는 서비스 메서드에 사용한다.