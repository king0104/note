#### 궁금증





### 왜 DFS가 백트래킹이 되어야 하는가?

- 가장 중요한 기본이 있다. DFS는 깊이 우선 탐색. 즉, 하나의 탐색을 끝까지 계속 해본 다음, 다음 탐색을 진행한다는 것이다.
- **하나의 탐색에 대해 쭈우우우우우욱 들어가서 결과를 만들어내고, 재귀가 끝나면 쭈우우우우우우우욱 빠져나와  두번째 탐색에 들어가는 것이다.** DFS 본질이 이렇게 쭈우우우우욱 들어갔다가 쭈우우우욱 나오는 것이므로, 필연적으로 백트래킹이 가능한 것이다.



#### 백트래킹

- 하나의 탐색을 쭈우우우우욱 진행하고, 탐색의 마지막 지점에서 다시 돌아오게 된다. **돌아오는 과정에서, 하나의 탐색을 진행하며 방문했던 값들을 다시 미방문 처리를 해주는 것이다.**
- 미방문 처리를 함으로서, 다음 두번째 탐색때에 이전 탐색 관련 값과는 전혀 상관없이 새로운 탐색을 진행할 수 있도록 도와준다.
- 미방문 처리를 하게 되므로, 하나의 visit 배열에 대해 여러번 재사용이 가능하다. 그래서, 메모리적으로 상당히 유리하다.
  - bfs 같은 경우 매번 visit 배열을 넘겨주며 각 탐색마다 새로운 visit 배열을 만들 수 있지만, 메모리적으로 불리하다.



#### 백트래킹 그림 + 코드 설명

![image-20220307165254388](C:\Users\4545a\AppData\Roaming\Typora\typora-user-images\image-20220307165254388.png)



#### 코드1 - 기본

- 백트래킹의 정의와 가장 닮아있는 코드



<코드 구성>

- **기본적으로 dfs와 동일 **
  - **다른 점 하나** : **현재 노드 기준으로 dfs가 모두 종료된 시점에, 현재 노드에서 퇴각한다는 의미를 지닌 코드가 추가되었다.**
  - 즉, **코드 마지막에 "현재 노드 미방문 처리"** 만 추가되었다.

```python
import sys
sys.setrecursionlimit(10 ** 5)

r, c = map(int, input().split())
plain = [list(map(lambda x: ord(x) - 65, input())) for _ in range(r)]

dy = [-1, 1, 0, 0]
dx = [0, 0, -1, 1]

alphabet = [False] * (26)
max_t = -1


def dfs(y, x, t):
    global max_t
    
    if alphabet[plain[y][x]]:
        return

    alphabet[plain[y][x]] = True
    max_t = max(max_t, t)

    for i in range(4):

        ny = y + dy[i]
        nx = x + dx[i]
        
        if 0 <= ny < r and 0 <= nx < c not alphabet[plain[ny][nx]]:
            dfs(ny, nx, t + 1)
    
    #########################################################################
    # 코드 상에서 이 부분은, 현재 노드에서 시작하는 dfs가 다 종료되면 도착하는 곳이다.
    # 그래서, 현재 노드에서 퇴각해야 하는 부분이다.
    # 따라서, 현재 노드를 미방문처리하는 부분이다.
    
    # 부연 설명을 하자면, 현재 노드에서 다음 노드로 가는 dfs가 전부 다 return 되면,
    # 현재 노드에서 더 이상 dfs가 불가능함을 뜻하므로, 현재노드에서 다음노드로 갈 수 없음을 뜻한다.
    # 따라서, 현재노드에서 퇴각한다 = 현재 노드 미방문처리
    alphabet[plain[y][x]] = False


dfs(0, 0, 1)
print(max_t)
```



---



#### 코드2 - 약간 변형

```python
import sys
sys.setrecursionlimit(10**5)

r,c = map(int,input().split())
plain = [ list(map(lambda x: ord(x) - 65, input())) for _ in range(r) ]

dy = [-1,1,0,0]
dx = [0,0,-1,1]

visit = [ [False]*(c) for _ in range(r) ]
alphabet = [False]*(26)
max_t = -1

def dfs(y,x,t):
    
    global max_t
    
    max_t = max(max_t,t)
    
    for i in range(4):
        
        ny = y + dy[i]
        nx = x + dx[i]
        
        if 0<=ny<r and 0<=nx<c and visit[ny][nx]==False and alphabet[plain[ny][nx]]==False:
            visit[ny][nx] = True
            alphabet[plain[ny][nx]] = True
            dfs(ny,nx,t+1)   
            visit[ny][nx] = False
            alphabet[plain[ny][nx]] = False                     

alphabet[plain[0][0]] = True
visit[0][0] = True

dfs(0,0,1)
print(max_t)
```

