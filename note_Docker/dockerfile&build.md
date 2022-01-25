### commit / build

- ![image-20220123234234861](C:\Users\4545a\AppData\Roaming\Typora\typora-user-images\image-20220123234234861.png)

#### 공통점

- image를 만든다

#### 차이점

- commit
  - 이미 사용하는 컨테이너를 이미지로 만드는, 
  - **백업**과 같은 느낌
- build
  - 도커 파일을 통해, 만들고 싶은 이미지를 구체적으로 (시간의 순서에 따라) 기록해서 만드는, 
  - 이미지를 **생성**하는 느낌
  - image가 어떤 과정을 통해 만들어지는지 분명하게 알 수 있다

---

#### commit

웹서버 이미지 만들기



#### build

1. dockerfile 만들기
   - FROM : file의 시작은 반드시 from
   - RUN : 운영체제에 명령을 전달하는 역할
     - 한번의 RUN마다 layer 생성



2. build 하기

- ```
  docker build [OPTIONS] PATH | URL | -
  ```

  - option
    - -t : build 할 image 이름 작성 가능
  - path
    - 내가 build하기 원하는 dockerfile 위치 적기
    - 현재 위치면, '.'
    - 다른 위치면, 다른 위치 적기
  

---

#### python3 설치 (웹서버 내장되어있어서 설치함.)

1. container에 직접 설치하기

   - ubuntu 실행 중인 컨테이너 접속 (docker exec -it ...)

   ---

   - apt update

   - apt install python3 하고, y 누르기

   ---

   - 웹브라우저가 접속할 경로 생성하기 & 경로로 이동하기
     - mkdir -p /var/www/html
       - (-p 옵션은, 존재하지 않는 경로라면 생성하라는 뜻)
     - cd /var/www/html

   ---

   - 위에서 설정한 경로에 index.html 파일 만들기
     - root@b495ba452804:/var/www/html# 에서,
     - echo "hello, <strong>Docker</strong/" > index.html

   ---

   - python3의 웹서버 실행하기
     - python3 -m http.server



2. dockerfile 만들어서 이미지 생성

   #### dockerfile 만들기

   1. FROM ubuntu:20.04

   ---

   - RUN apt update && apt install -y python3

   ---

   - WORKDIR /var/www/html

   ---

   - host에 index.html 이라는 파일을 만들고, container에서 해당 파일을 복사하기
     - index.html 파일 생성하기
       - 내부 내용 : hello, <strong>Docker</strong/>
     - COPY ["index.html","."]
       - host의 index.html 파일을, container의 현재 디렉토리(/var/www/html)으로 copy해라 

   ---

   - CMD ["python3", "-u", "-m","http.server"]

   ---

   ---

   #### build

   - docker build -t web-server-build .;
   - docker rm -f web-server
   - docker run -p 8888:8000 --name web-server web-server-build



---

#### RUN vs CMD

RUN

- build가 되면서 실행되는 명령어
- 즉, image에 반영

CMD

- 컨테이너가 실행될 때 실행되는 명령어
- 즉, container에 반영

- tip - image를 만들면서 바로 cmd가 실행되는 것을 원치 않을 때)
  - docker run 마지막에 pwd 명령어 주면 된다.
  - docker run -p 8888:8000 --name web-server web-server-build -pwd