## reset

내가 현재 checkout하고 있는 branch의 최신 커밋을 바꾸는 작업

아주 간단한 행위일 뿐이다.



#### reset한 내용 취소하기

git reflog로 내역 확인







## checkout

1. git checkout [branch]

   - checkout의 역할을 제대로 알고 사용한 것. 

   - **브랜치를 바꾸는 것**이 checkout이다.





2. git checkout "commit"

   - checkout의 역할을 제대로 모르고 사용. 커밋으로 checkout 함

   - detached head 발생
     - head가 브랜치를 가리키는 것이 아니라, 커밋을 직접 가리키고 있는 상태