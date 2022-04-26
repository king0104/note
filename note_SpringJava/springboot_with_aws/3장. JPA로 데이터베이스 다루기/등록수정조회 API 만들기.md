### 등록/수정/조회 API 만들기

#### API 만들기 위한 3개의 클래스

1. request 데이터 받기 위한 dto
2. API 요청 받을 controller
3. 트랜잭션, 도메인 기능 간의 순서를 보장하는 service



1,2 -> web 패키지

3 -> service 패키지



---

#### API 만드는 과정

1. controller 만들기
2. service 만들기
3. dto 만들기

---

#### 1. controller 만들기





---

#### 2. service 만들기

트랜잭션과 도메인 간 순서 보장 역할



---

#### 3. controller/service에서 사용할 dto 만들기

#### 3-1. Entity vs DTO

- Entity와 매우 유사하지만, 하나 더 만들었다

- Entity 클래스는 절대로 Request/Response 클래스로 사용해서는 안되기 때문!!!!!!!

---

**<Entity 클래스> : DB layer와 맞닿음**

- DB와 직접적으로 맞닿은 핵심 클래스이다.
- 엔티티 클래스를 기준으로 테이블이 생성되고, 스키마가 변경되기도 한다.
  - 화면 변경은 아주 사소한데, 테이블과 연결된 엔티티 클래스를 변경하는 것은 매우 큰 변경이기 때문에, DTO를 만들어야 한다.
  - 즉, **Entity 클래스는 절대로 Request/Response 클래스로 사용해서는 안된다**



**<dto 클래스> : View layer와 맞닿음**

- request / response 용으로 사용되는 클래스이다
- View를 위한 클래스이다.
- controller, service에서 사용함

---

=> DB layer / View layer의 역할 분리를 철저하게 해야 한다!!!

#### 3-2. DTO 만드는 방법

1. 어노테이션
   - Getter
   - NoArgsContstructor (builder 패턴으로 전체 필드 존재 시 생성자를 만드니까 NoArgesConstructor 만듬)
2. Entity의 필드 중, 필요한 필드만 필드로 정의하기
3. dto 생성자 -> 빌더 패턴
4. dto to Entity -> 빌더 패턴으로 toEntity() 작성

```java
@Getter
@NoArgsConstructor
public class PostsSaveRequestDto {
    private String title;
    private String content;
    private String author;

    @Builder
    public PostsSaveRequestDto(String title, String content, String author) {
        this.title = title;
        this.content = content;
        this.author = author;
    }

    public Posts toEntity() {
        return Posts.builder()
                .title(title)
                .content(content)
                .author(author)
                .build();
    }
}
```
