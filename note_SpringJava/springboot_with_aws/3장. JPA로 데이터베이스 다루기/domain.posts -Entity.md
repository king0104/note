### Posts

#### @Entity

- 엔티티 클래스
- 실제 db와 매칭될 클래스
- **절대로 setter 메서드를 만들지 않는다!!!!!!!**



#### 엔티티 클래스를 생성하는 방식

1. 생성자

   - alt+insert로 생성자 만들기

   - 사용 방법 : new

   

2. @builder

   - alt + insert로 생성자 만들기 + @Builder 어노테이션 붙이기!!!

     - ```java
       @Builder
       public Posts(String title, String content, String author) {
           this.title = title;
           this.content = content;
           this.author = author;
       }
       ```

   - 사용 방법 : 엔티티.builder() 사용

     - ```java
       postsRepository.save(Posts.builder()
               .title(title)
               .content(content)
               .author("yoon@naver.com")
               .build());
       ```

       



#### 엔티티 클래스에 값을 채워 DB에 삽입하는 방식은?

- 기본 : 생성자를 통해 최종 값을 채운 후, DB에 삽입

  - ```java
    postsRepository.save(new Posts(title, content, "yoon"));
    ```

- **응용 : 생성자 대신, @Builder 사용 -> 적극적으로 사용할 예정**

  - ```java
    postsRepository.save(Posts.builder()
            .title(title)
            .content(content)
            .author("yoon@naver.com")
            .build());
    ```



- 값 변경 필요 시 : 해당 이벤트에 맞는 public 메서드 호출하여 값 변경



#### lombok의 어노테이션

- @NoArgsConstructor
- @Getter
- @Builder

