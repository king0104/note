#### tip) stage 상태로 보존한다는 것의 의미

- 맨 처음엔 다음과 같은 상태라고 하자. 여기서 git reset --soft 1438을 하면 어떻게 되는지 살펴보자.

![image-20220428115323358](C:\Users\4545a\AppData\Roaming\Typora\typora-user-images\image-20220428115323358.png)



- 아래와 같이 uncommited change가 존재하지만, main branch는 이전 커밋으로 되돌아간 것을 볼 수 있다. 이것이 stage 상태이다. **즉, 이전 커밋으로 돌아가지만 현재 코드는 남겨둔다는 뜻이다.**

![image-20220428115042381](C:\Users\4545a\AppData\Roaming\Typora\typora-user-images\image-20220428115042381.png)

