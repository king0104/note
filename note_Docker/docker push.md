### docker push

docker 공유하기,  push

- ![image-20220124022454706](C:\Users\4545a\AppData\Roaming\Typora\typora-user-images\image-20220124022454706.png)





1. docker hub에서 repository 생성
   - ![image-20220124022744727](C:\Users\4545a\AppData\Roaming\Typora\typora-user-images\image-20220124022744727.png)

2. docker image 실행(run) 및 컨테이너에서 원하는 작업 수행.

   - ```
      docker run -it --name my-python ubuntu
     ```

   - 접속한 컨테이너에 python3 설치

     - ```
       apt update && apt install python3
       ```

     

3. 실행한 container로 image 만들기 (=commit)

   - ```
     docker commit my-python 4545abc/python3:1.0 
     ```



이제, docker hub에 올려야 한다

1. 도커에 로그인

   - ```
     docker login
     ```

2. docker hub에 push

   - ```
     docker push 4545abc/python3:1.0
     ```

     

