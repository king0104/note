## assertThat의 다양한 쓰임새

#### 날짜 비교하기

- isAfter( 시간 ) : 시간 이라는 LocalDateTime보다 미래인지

    - ```java
      LocalDateTime now = LocalDateTime.of(2019,6,4,0,0,0);
      
      assertThat(posts.getCreatedDate()).isAfter(now);
      assertThat(posts.getModifiedDate()).isAfter(now);
    
    



#### 엔티티의 내용 비교하기

- isEqualTo( 내용 )

    - ```java
    assertThat(post.getTitle()).isEqualTo(title);
    assertThat(post.getContent()).isEqualTo(content);
    
    

- get(0) & isEqualTo(내용)

    - ```
      List<Posts> all = postsRepository.findAll();
      assertThat(all.get(0).getTitle()).isEqualTo(title);
      assertThat(all.get(0).getContent()).isEqualTo(content);
      ```