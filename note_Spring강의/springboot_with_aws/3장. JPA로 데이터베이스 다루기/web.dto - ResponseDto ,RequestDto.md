## ResponseDto

만든 dto

- PostsResponseDto



<만드는 방식>

- 이름 
  - 도메인 + response
  
- 필드

  - 원하는 필드

- 메서드

  응답 객체는, 진짜 할 일이 **"dto를 만들어 응답하는 것"** 말고는 할 일이 없다. 그래서 메서드가 생성자 하나밖에 없다.

  - **생성자 방식 사용**
  - **생성자의 매개변수는, entity가 된다.** 이유는 간단하다. 응답이라는 의미가 db에서 값을 가져와서 사용자에게 전달해준다는 뜻이다. 이때, db에서 가져오는 값은 entity 클래스가 된다. 따라서, 그 entity를 받아서 dto를 생성하는 것이기 때문에, 생성자의 매개변수는 entity가 된다.



<특징>

- 하나의 도메인에 대해 responseDto는 하나만 있으면 된다.



## RequestDto

<만든 dto>

- PostsSaveRequestDto

- PostsUpdateRequestDto



<만드는 방식>

- 이름
  - 도메인 + 기능 + request



<특징>

- 하나의 도메인에 대해, 여러 개의 requestDto가 필요하다
  - 이유 : 컨트롤러에 작성한 기능 하나당 requestDto 하나가 필요한데, 하나의 도메인에 대해 최소한 CRUD를 진행하는 것이 기본적이라, 기능은 최소 2개 이상이다.  그래서 여러개의 requestDto가 생성된다.

