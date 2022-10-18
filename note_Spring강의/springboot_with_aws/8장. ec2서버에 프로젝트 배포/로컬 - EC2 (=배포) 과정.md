## 로컬 -> EC2 배포 과정

<로컬>

1. 스프링 부트 프로젝트 제작
2. 로컬에서 잘 돌아가는지 확인



<EC2 / RDS>

1. 깃허브에 프로젝트 올리기
2. putty로 ec2 접속 -> git clone 통해 프로젝트 다운받기
3. ec2 /  RDS 사용 위한 추가 설정들 하기
   1. application-oauth.properties 생성
   2. H2 -> RDS로 db 바꾸기
      - application-real-db.properties 생성

4. **deploy.sh 통해 프로젝트 배포**



