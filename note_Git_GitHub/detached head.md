## git 관련

#### 특정 버전으로 돌아가기

- 특정 버전으로 돌아가기 전에, 현재 상태 커밋해주어야 한다.

< 돌아가는 방법>

1. 단계별로 돌아가기

   - git checkout head~1(1이면, 1단계 전으로 돌아가기)

2. 특정 커밋으로 짚어서 돌아가기

   - git log 로 돌아가고 싶은 커밋의 해시코드 확인하기
   - "git checkout 복사한 해시코드"

   

- 이전 버전으로 돌아가 수정한 후, 해당 버전에 수정사항을 반영할 수 있나요?

#### detached HEAD

- feedproject6-2를 커밋하고, 푸시를 진행했는데 6-1이 푸시가 되었다. 소스트리에서 확인해보니 아래와 같은데, head는 뭐고 다른 표시들은 뭘까??

- ![](C:\Users\4545a\AppData\Roaming\Typora\typora-user-images\image-20211117201505657.png)

  - head의 의미

    - **하나의 branch를 가리키는(참조하는) 태그 비슷한 것.**
    - 여기서 branch란?
      - source tree의 최상단 커밋을 참조하는 것. 이라고 생각하자.
    - head가 존재함으로써, branch의 마지막(최상단) commit이 아닌 이전 commit에 checkout 할 수 있다.

  - **detached HEAD**

    - branch를 가리키지 않고, 직접적으로 특정 commit을 가리키고 있는 상황

    - (원래는 이름이 있는 branch를 가리키고 있어야 한다)

    - 어쨌든 detached HEAD에서 커밋이 가능하다. 브랜치 없는 커밋이 충분히 만들어질 수 있다는 것이다. **그 커밋은 붕붕 떠있는 상황이고, 브랜치가 없어 `push`가 되지 않고 버전관리가 불가능하다.**

      **이미 branch없이 붕붕 떠있는 커밋이 생겼다면, 브랜치에 커밋을 안정적으로 붙여줘야한다.**

    - **[detached HEAD 해결법 - 내 언어]**

    - 1. 임시 **브랜치 만들고**
      2. 임시 브랜치에 둥둥 떠다니는 커밋 **붙이기**
      3. 기존 브랜치에 **머지**
      4. 임시 브랜치는 삭제

    - **[detached HEAD 해결법 - 외부 블로그]**

    - 임시 브랜치를 만들어 합치기

      - `git checkout -b 임시브랜치` (새로운)임시 브랜치 만들어 체크아웃
      - `git checkout 정착할 브랜치` 정착할 브랜치(보통 master)로 이동
      - `git merge 임시브랜치` 정착할 브랜치에 임시브랜치 머지
      - `git branch -d 임시브랜치` 필요없다면 임시브랜치 삭제

    - 기존 브랜치에 커밋 붙이기

      - `git reflog`로 둥둥 떠다니는 커밋의 id를 확인
      - `git checkout 기존브랜치` 기존 브랜치로 이동
      - `git cherry-pick 커밋id` 떠다니던 커밋 기존브랜치에 붙이기

방법이 어떠하든 결국 둥둥 떠있는 커밋을 브랜치에 붙이는게(?) 포인트이다!