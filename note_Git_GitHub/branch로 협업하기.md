## branch

- 미리 작업공간 나눠두고, 한번에 합치자!

![image-20210722024900268](C:\Users\4545a\AppData\Roaming\Typora\typora-user-images\image-20210722024900268.png)

1. 작업 공간 나누기

   - 1번 사람 - 그대로 d커밋을 진행

   - 2번 사람 - 새로운 브랜치를 만든다 -> q커밋 진행

2. 이후에는, 각자의 브랜치에서 계속 커밋 진행

3. **merge** 

   - 2개의 공간에서 개발된 코드를 하나의 브랜치로 합치기
   - 이때, 같은 파일, 같은 라인을 수정했다면 conflict 해결 해줘야 한다.
   - github에서는, PR(pull request)



---

### branch 만들기

- **git branch** - 브랜치들을 보여준다
  - ![image-20210722145242768](C:\Users\4545a\AppData\Roaming\Typora\typora-user-images\image-20210722145242768.png)
- **git branch 브랜치이름** - 해당 브랜치를 만든다
  - ![image-20210722145227872](C:\Users\4545a\AppData\Roaming\Typora\typora-user-images\image-20210722145227872.png)
- **git checkout 브랜치이름** - 해당 브랜치로 이동한다
  - ![image-20210722145303264](C:\Users\4545a\AppData\Roaming\Typora\typora-user-images\image-20210722145303264.png)



---

### github에 올리기

- **git push origin main**
  - ![image-20210722150456589](C:\Users\4545a\AppData\Roaming\Typora\typora-user-images\image-20210722150456589.png)

- **git push origin 브랜치이름**

  - ![image-20210722150554059](C:\Users\4545a\AppData\Roaming\Typora\typora-user-images\image-20210722150554059.png)

  - 아래와 같이 브랜치가 하나 생성된 것을 알 수 있다.
    - ![image-20210722150712748](C:\Users\4545a\AppData\Roaming\Typora\typora-user-images\image-20210722150712748.png)
  - 메인과 브랜치 간 비교 후 pull request 할거냐 뜬다.
    - ![image-20210722150731517](C:\Users\4545a\AppData\Roaming\Typora\typora-user-images\image-20210722150731517.png)

---

### main에 branch 합치기 (PR 혹은 merge라고 불리는 과정)

1. pull request 들어가기
   - ![image-20210722151037131](C:\Users\4545a\AppData\Roaming\Typora\typora-user-images\image-20210722151037131.png)

2. new pull request 누르기

   - ![image-20210722151102510](C:\Users\4545a\AppData\Roaming\Typora\typora-user-images\image-20210722151102510.png)

3. compare changes

   - 베이스를 어떤 것을 하고 어떤 것을 compare해서 넣을 것이냐?
     - ![image-20210722151150793](C:\Users\4545a\AppData\Roaming\Typora\typora-user-images\image-20210722151150793.png)

   - 아래와 같은 것이 다름. 
     - ![image-20210722151344921](C:\Users\4545a\AppData\Roaming\Typora\typora-user-images\image-20210722151344921.png)

4. create pull request

   - ![image-20210722151509413](C:\Users\4545a\AppData\Roaming\Typora\typora-user-images\image-20210722151509413.png)

5. pull request 날리기
   - main을 수정하는 것이기 때문에 이름 잘 붙이기
   - 아래에는 어떤 것을 수정했는지 적어주기
     - ![image-20210722151712452](C:\Users\4545a\AppData\Roaming\Typora\typora-user-images\image-20210722151712452.png)

6. 최종적으로 main에 branch 추가하기(**merge**)

   - ![image-20210722152208852](C:\Users\4545a\AppData\Roaming\Typora\typora-user-images\image-20210722152208852.png)

   - merge 하기
     - ![image-20210722152242046](C:\Users\4545a\AppData\Roaming\Typora\typora-user-images\image-20210722152242046.png)



---

#### *TIP*

- **새로운 브랜치**를 만든다는 것 = **새로운 파일**을 만든다는 것. ( **브랜치 = 파일** )
  - 그래서 브랜치를 main에 추가할 때,
    - ![image-20210722152500998](C:\Users\4545a\AppData\Roaming\Typora\typora-user-images\image-20210722152500998.png)
    - 위와 같은 말이 사용된다