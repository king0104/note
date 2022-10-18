## 1. Entity, Repository 클래스 만들기

1. 가장 먼저, domain 패키지/특정 엔티티명 패키지 를 만든다

2. 그 다음, 해당 [엔티티 클래스]와 엔티티 클래스를 DB와 연결시켜줄 [Repository클래스]를 작성한다
   - spring data jpa를 사용해서, JpaRepository를 사용한다
   - ![image-20220627191717773](/Users/yoon/Library/Application Support/typora-user-images/image-20220627191717773.png)

<구조>

![image-20220627191933085](/Users/yoon/Library/Application Support/typora-user-images/image-20220627191933085.png)



#### 1-2. repository 기능 test하기







## 2. Controller, Service, dto 클래스 만들기

- 궁금점

  컨트롤러, 서비스, dto중, 어떤 클래스를 먼저 만드는 것인가..?



#### Controller 



#### Service



#### Dto 클래스 만드는 방법

- view를 위한 클래스이므로, 엔티티 클래스와 역할 분리 철저히!



##### EntitySaveRequestDto

- **값을 받아서 -> dto를 만들고** -> db 저장시 엔티티로 저장

@Getter

@NoArgsConstructor

1. 원하는 값을 필드로 갖기
2. 생성자 만들기 : Builder 패턴 (값 -> dto)
3. toEntity() 작성 (dto -> 엔티티 클래스)



##### EntityResponseDto

- id값을 받아서 -> db에서 원하는 엔티티를 찾은 후 -> **엔티티를 이용해 dto를 만들어** -> 뷰로 리턴

@Getter

1. 엔티티의 값을 필드로 갖기
2. 생성자 만들기(엔티티 -> dto)



##### EntityUpdateRequestDto

- 변경하기를 원하는 필드 값을 받아서 -> dto 만들기

@Getter

@NoArgsConstructor

1. 원하는 값 필드로 받기
2. 생성자 만들기 : Builder 패턴(값 -> dot)



<구조>

![image-20220627191246400](/Users/yoon/Library/Application Support/typora-user-images/image-20220627191246400.png)



#### Controller 클래스 test하기

- @SpringBootTest
- TestRestTemplate 이용하기





