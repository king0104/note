## 에러 해결

- Travis CI 에서 에러 발생
  - ![image-20220525095858455](C:\Users\4545a\AppData\Roaming\Typora\typora-user-images\image-20220525095858455.png)



- 다른 사람들의 해결 방법
  1. appspec.yml 파일 에러
  2. CodeDeploy 그룹의 태그 잘못 입력
  3. .travis.yml 파일 에러



- 내 에러 확인하기
  - 배포 - 배포 ID 클릭
    - ![image-20220525100024850](C:\Users\4545a\AppData\Roaming\Typora\typora-user-images\image-20220525100024850.png)
  - 배포 수명 주기 이벤트 - 이벤트 클릭
    - ![image-20220525100129966](C:\Users\4545a\AppData\Roaming\Typora\typora-user-images\image-20220525100129966.png)
  - 에러 확인
    - ![image-20220525100159511](C:\Users\4545a\AppData\Roaming\Typora\typora-user-images\image-20220525100159511.png)



- 에러 해결
- The CodeDeploy agent did not find an AppSpec file within the unpacked revision directory at revision-relative path "appspec.yml". 
  - appspec.yml을 찾을 수 없다고 나왔다.
  - 실제로, 내가 appspec을 root 경로에 두지 않고, /src 경로에 두어서 발생한 문제였다!!!