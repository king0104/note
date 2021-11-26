## RestTemplate

- 기초 작업
  - @test에 관련된 포스팅
    - test는 어디에 위치해야 하는가
    - 





- 왜 계속 nullpointerexception이 뜨는가?

  - 해결 : @RunWith(SpringRunner.class) 사용
  - @RunWith(SpringRunner.class) 란?
    - jnuit 4에서 사용하는 것

  

- api를 만들때 return 타입을 ResponseEntity로 해야 작동하는건가요? 아니면 그런건 상관 없는건가요?

  - 상관없음



- 혼자 알게 된 내용

  - resttemplate을 사용해서 적는 코드는 cilent측이라고 생각하면 된다.
  - controller 만드는 부분, 즉 api를 만드는 부분이 server측이라고 생각하면 된다.
  - resttemplate -> controller 요청

  - ResponseEntity
    - Httpheader, HttpBody 같은 정보까지 받을 수 있는 더 정교한 리턴타입(?)



- requestBody에 resttemplate으로 데이터 전달하는 방법은??

- Remember, we want to post the data in JSON format. In order to that, **we added the \*consumes\* attribute in the \*@PostMapping\* annotation with the value of “application/json”** for both methods.

  Similarly, we set the *produces* attribute to “application/json” to tell Spring that we want the response body in JSON format.

  We annotated the *person* parameter with the [*@RequestBody*](https://www.baeldung.com/spring-request-response-body) annotation for both methods. This will tell Spring that the *person* object will be bound to the body of the *HTTP* request.

  

  

  .