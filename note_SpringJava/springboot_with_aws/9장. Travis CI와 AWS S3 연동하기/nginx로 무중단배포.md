## nginx

#### 동작구조

![image-20220528153125082](C:\Users\4545a\AppData\Roaming\Typora\typora-user-images\image-20220528153125082.png)

1. 사용자는 서비스 주소로 접속 (http의 경우 80 포트, https의 경우 443 포트)
2. Nginx는 사용자 요청을 받아 현재 연결된 Spring boot로 요청 전달
3. 두 번째 Spring boot는 연결되어 있지 않아 요청받지 못한다.



신규 배포가 필요한 경우

1. 연결되지 않은, 두 번째 Spring boot에 배포를 한다. (Nginx는 첫 번째 Spring boot와 연결된 상태라 서비스가 중단되지 않는다.)

2. 배포 후에 정상적으로 두 번째 Spring boot가 구동 중인지 확인
3. 2가 정상적이라면, nignx reload 명령어를 통해 Nginx 연결을 2와 연결

