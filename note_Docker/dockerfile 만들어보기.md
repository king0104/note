그러면 본격적으로 Dockerfile를 작성해보도록 하겠습니다.

Dockerfile은 텍스트 형식이며, 파일명 또한 "**Dockerfile**" 입니다. 확장자는 따로 존재하지 않습니다.



#### 궁금증

- dockerfile은 그냥 파일명 자체를 Dockerfile로 하는 건가요?
  - Dockerfile로 할 시
    - 경로 통해 어떤 도커파일 빌드할 지 결정하는 것
    - docker build -t 1223yys/web-project:latest .

  - Dockerfile 이외의 다른 이름으로 할 때
    - 파일명 다르게 하면, https://coding-start.tistory.com/341 참고
    - docker build -t 1223yys/web-project -f ./custom_file_name .






- 왜 centos 이미지는 run이 안되냐?



#### 명령어

- FROM

  - base 이미지

  - ```dockerfile
    FROM <이미지>
    FROM <이미지>:<태그>
    ```

- WORKDIR
  - 컨테이너 내 경로 지정하기(해당 경로가 현재 내가 위치한 경로가 된다.)
  - 경로를 지정했다는 것 = 내가 위치한 경로라는 것 = 뒤에 실행될 명령어는 지금 위치한 경로에서 실행될 것이라는 것
  - (copy보다 workdir 먼저 하니까 오류 안남. 정확히는 모르지만, **일단 workdir -> copy 순으로 명령어 작성하자.)**
  
- COPY

  - 호스트 컴퓨터에서, 도커 이미지의 파일 시스템으로 파일(또는 디렉토리) 이동

  - ```dockerfile
    COPY <src>... <dest>
    ```

- CMD

  - 이미지를 컨테이너로 띄울 때. 즉, run 할 때, 딱 한번 실행되는 명령어
  - 디폴트로 실행될 명령어 / ENTRYPOINT로 지정한 명령어에 디폴트로 넘길 파라미터 지정
  - docker run 할 때, 인자 있으면 실행 안됨.