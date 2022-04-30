## push 취소하기

문제 상황 : push를 해서는 안되는 client secret 정보를 push 해버렸다. git은 똑같이 유지하되, github에 push한 것만 지우고 싶다



push 취소하기를 검색하면, 방법 2가지가 나온다. 아래와 같으며, 사실 내 문제 상황에서는 방법 1이 적합하다. 방법 2는 커밋을 삭제하는 것이 아니기 때문이다. (커밋 전부 남기고, 이전 코드를 새로운 커밋으로 추가하는 것임)



### 방법 1 : git reset

1. git을 되돌리고 싶은 커밋으로 되돌리기
   - git reset 사용
   - **현재 내용을 stage 상태로 보존**하면서 reset 할 것인가 / 현재 내용을 아예 삭제할 것인가에 따라서 옵션 사용 
     - **--soft  / --hard**
2. 되돌린 커밋을 github에 push하기
   - origin에 없는 내용을 commit하기 때문에, 오류가 난다. 따라서 **--force 옵션**으로 강제로 push 해야 한다.



#### tip) stage 상태로 보존한다는 것의 의미

- 맨 처음엔 다음과 같은 상태라고 하자. 여기서 git reset --soft 1438을 하면 어떻게 되는지 살펴보자.

![image-20220428115323358](C:\Users\4545a\AppData\Roaming\Typora\typora-user-images\image-20220428115323358.png)



- 아래와 같이 uncommited change가 존재하지만, main branch는 이전 커밋으로 되돌아간 것을 볼 수 있다. 이것이 stage 상태이다. **즉, 이전 커밋으로 돌아가지만 현재 코드는 남겨둔다는 뜻이다.**

![image-20220428115042381](C:\Users\4545a\AppData\Roaming\Typora\typora-user-images\image-20220428115042381.png)



---

### 방법 2 : git revert

revert는 reset과 다르게 커밋을 삭제하는 것이 아닌 커밋을 추가합니다.

그러나 이전 커밋과 정반대의 데이터를 추가하는 방식으로 코드를 되돌립니다.

**즉, 커밋을 삭제하는 것이 아니라, 되돌린 코드에 대한 커밋을 추가한다는 뜻이다.**



아래의 블로그가 매우 잘 정리되어 있으므로, 참고하자.

https://kyounghwan01.github.io/blog/etc/git/git-reset-revert/#reset



만화정리

https://www.popit.kr/%EA%B0%9C%EB%B0%9C%EB%B0%94%EB%B3%B4%EB%93%A4-git-back-to-the-future/

