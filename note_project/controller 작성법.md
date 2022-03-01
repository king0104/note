## Controller

#### DTO 관련

- client와 직접 맞닿아있는 곳이기 때문에, DTO로 통신하게 된다
  - 컨트롤러라는, 클라이언트가 접근한다는 특성상 dto라는 객체가 만들어지는 것이기 때문에(엔티티에 직접 접근을 막는다), 컨트롤러 패키지 안에 dto 패키지를 넣기도 한다
  - ![image-20220228221643691](C:\Users\4545a\AppData\Roaming\Typora\typora-user-images\image-20220228221643691.png)



- DTO는 @Getter, @NoArgsConstructor, @AllArgsConstructor, @Builder(선택) 이정도 붙이는 듯. **@Setter가 없음을 명심하자**
- api를 기능 별로 만드니까(controller-service-repo와 같은 하나의 흐름), 그에 따른 **dto도 기능 별로 하나씩 필요하게 된다.**

----

- return은 ResponseEntity를 사용하는 편.

  - ```java
    @GetMapping("/me")
    public ResponseEntity<MemberResponseDto> getMyMemberInfo() {
            return ResponseEntity.ok(memberService.getMyInfo());
    }
    ```

    

- 경로 작성 시, 생각 잘 하기
  - restapi가 어떻게 이루어져있는지 생각하면 된다. 자원명으로 경로가 이루어져야한(? 수정필요)



- api를 기능 별로 만드니까, 그에 따른 dto도 기능 별로 하나씩 필요하게 된다.