### git config : 유저 네임, 유저 이메일 바꾸기

- 깃허브 아이디, 이메일과 *같은 이름*으로 해야지 나중에 깃허브와 연동 가능

![image-20210721174251859](C:\Users\4545a\AppData\Roaming\Typora\typora-user-images\image-20210721174251859.png)



---

- 폴더에서 cmd 치면 -> 바로 그 터미널로 이동
- cd
- cd ..
- mkdir

---



### git init / git add / git commit / git log

1. 사진사 고용

2. 사진 찍힐 사람들 만들기

3. 사진 찍기

   

- git log :  git에 commit한 버전들 확인

+ git status : 현재 상태 확인용

---

### 로컬에서의 버전관리(형상 관리) with 메모장

0. cmd창 열기

1. 버전 관리를 하고 싶은 폴더로 이동
2. 폴더에 사진사 고용 **git init**
   - git staus : 현재 상태 확인용 - 사진 찍을 사람들 모였나? - 안모이면 빨간색
   - ![image-20210721174403709](C:\Users\4545a\AppData\Roaming\Typora\typora-user-images\image-20210721174403709.png)
3. 사진 찍힐 사람들 모으기 **git add**
   - git status : 현재 상태 확인용 - 사진 찍을 사람들 모였나? - 모였으면 초록색
   - ![image-20210721174420195](C:\Users\4545a\AppData\Roaming\Typora\typora-user-images\image-20210721174420195.png)
4. 사진 찍기 **git commit**
   - git commit -m "블라블라블라" : 사진 제목을 정하는 것
   - ![image-20210721174339727](C:\Users\4545a\AppData\Roaming\Typora\typora-user-images\image-20210721174339727.png)
5. 사진 잘 찍혔나 확인 **git log**
   - ![image-20210721174326666](C:\Users\4545a\AppData\Roaming\Typora\typora-user-images\image-20210721174326666.png)



- 특정 버전으로 돌아가기 **git reset --hard blablabla(git log쳐서 나오는 커밋 링크(?))**
  - ![image-20210721174458775](C:\Users\4545a\AppData\Roaming\Typora\typora-user-images\image-20210721174458775.png)

- 마지막 수정 사항 지우기 **git reset --hard**



---

### github 가입 후 리모트에 연동시키기

#### git에서 github로 올리기(push)

1. github에서 repository 생성
2. ![image-20210721182153953](C:\Users\4545a\AppData\Roaming\Typora\typora-user-images\image-20210721182153953.png)
   - **git remote add origin 레포지토리 주소** 명령어 실행 : **리포지토리와 내 로컬 폴더 연결**

3. **git push origin main**

   - git에 commit한 내용을 repository에 push 하는 과정

   - ![image-20210721182516055](C:\Users\4545a\AppData\Roaming\Typora\typora-user-images\image-20210721182516055.png)



---

 #### github의 모든 커밋을 로컬로 가져오기(clone)

1. 원하는 버전(commit) 들어가기
2. clone 눌러서 주소 복사
3. **git clone 리포지토리 주소(복사한 주소)**

---

#### github에서 바꾼 값만 로컬로 가져오기(pull)

1. **git pull origin main**
   - ![image-20210721184107340](C:\Users\4545a\AppData\Roaming\Typora\typora-user-images\image-20210721184107340.png)



---

#### git에서 해당 폴더의 버전을 바꾸기 위한 방법

1. git에서 직접 하기
   - ㄴ**git log** 명령어를 통해 원하는 버전(원하는 커밋)의 주소 확인 - 복사
   - **git reset --hard 원하는 버전의 주소** 
2. github에서 로컬로 가져오기
   - github에서 원하는 버전(원하는 커밋)의 주소 확인 - 복사(=클론)
   - **git reset --hard 원하는 버전의 주소**



---

![image-20210721185210313](C:\Users\4545a\AppData\Roaming\Typora\typora-user-images\image-20210721185210313.png)

- 이 그림 이해되면, 기본 git, github 사용 끝!
