## 첫 과제

자바의 정석 책의 예제 코드를 받아서 내 github에 올리는 것이 과제다.



간단하게 말하면,

1. 자바의 정석 github 들어가서 레포지토리 클론하기
2. 내 폴더에 클론하기
3. 폴더 내의 source 폴더를 github에 push하기

의 순으로 진행하면 된다.



#### 실제 진행 과정

1. 자바의 정석 github에서 **레포지토리를 클론**한다

   ![image-20210721193359513](C:\Users\4545a\AppData\Roaming\Typora\typora-user-images\image-20210721193359513.png)

   - 클론을 진행할 폴더에  **git init**을 통해 해당 폴더가 git을 사용하도록 한다.
   - **git clone 레포지토리 주소**를 통해 레포지토리를 받아온다

   

2. 클론한 폴더에서, source 폴더로 들어간다.

   - **git init**을 통해 source 폴더가 git을 사용하도록 한다. - 사진사 고용
   - **git add .** : source 폴더 내의 모든 내용을 모은다 - 사진 찍을 사람 모으기
   - **git commit -m "  "** : 내 로컬에 커밋을 진행한다 - 사진 찍기



3. source 폴더와, 내 github의 레포지토리를 연동한다.

   - github에서 레포지토리 생성
   - **git remote add origin 레포지토리 주소** 명령어 실행 : **리포지토리와 내 로컬 폴더 연결**

   - **git push origin main** : git에 커밋한 내용을 github에 올리기



