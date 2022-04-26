## ResponseDto

만든 dto

- PostsResponseDto



<만드는 방식>

- 이름 
  - 도메인 + response



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

