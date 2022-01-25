```java
/**
 * DTO
 *  - 순수 클래스
 *  - getter만 필요.
 */
@Getter
public class CreateItemDto {
    private String name;
    private String brand;

    /**
     * DTO -> entity
     * - 빌더 패턴을 사용하자
     */
    // 빌더 패턴 사용
    public Item toEntity() {
        return Item.builder()
                .id(null)
                .name(this.name)
                .brand(this.brand)
                .build();
    }

}
```

### DTO

- 주로 **각 기능마다 필요로 하는 필드들을 모은** **DTO 클래스**를 만들어 받습니다.
- 그래서 dto 이름 또한, **createItemDto 와 같이 기능적인 부분이 들어가야 한다.**
- 질문 : dto를 만들때 엔티티의 컬럼에 들어가있지 않은 필드값을 넣기도 하나요?

####  DTO 필드

- 컬럼
  - **원하는 기능에 필요한 파라미터만**을 컬럼으로 가진다 ( 엔티티 객체 컬럼의 일부만을 필드로 갖는다는 뜻)

- 메서드

  - **toEntity()**

    - DTO -> entity 를 만들어주는 메서드임

    - 빌더 패턴으로 작성하면 됨

      1. entity 객체에 @Builder 어노테이션 추가
      2. dto 클래스에 toEntity() 메서드 추가

      - ```java
            // 빌더 패턴 사용
            public Item toEntity() {
                return Item.builder()
                        .id(null)
                        .name(this.name)
                        .brand(this.brand)
                        .build();
            }
        ```

        



#### DTO 사용 범위

- dto 는 언제까지 쓰는건지??
  - **컨트롤러까지...**
  - 컨트롤러에서  dto -> 도메인 객체로 변환하는 것이 좋겠다.



