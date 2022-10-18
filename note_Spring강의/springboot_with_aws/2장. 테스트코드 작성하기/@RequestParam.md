### @RequestParam

- 외부에서 API로 넘긴 파라미터를 가져오는 어노테이션

- ```java
  @GetMapping("/hello/dto")
  public HelloResponseDto helloDto(@RequestParam("name") String name,
                                   @RequestParam("amount") int amount) {
      return new HelloResponseDto(name, amount);
  }
  ```

  - 외부에서 name으로 받은 파라미터 -> 코드 내부에서 name으로 사용
  - 외부에서 amount으로 받은 파라미터 -> 코드 내부에서 amount으로 사용

