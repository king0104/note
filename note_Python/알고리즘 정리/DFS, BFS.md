### 개념 : DFS or BFS

- 문제에 적용할 때, 아무거나 적용해도 되는 경우가 대부분. 어떻게 하던지 탐색을 하는 경우라면, 둘 다 사용할 수 있다. 여기서, 조금 나누자면 다음과 같다.

#### dfs

- 어떻게 하던지 간에 탐색을 하면 되는 경우

- 팁)
  - pypy3로 메모리 초과난다 -> sys.setrecursionlimit(10**5) 로 바꾸기

#### bfs

- **탐색에 순서가 있는 경우**. 한 칸 다음 다음 3칸 탐색 이런식으로 순서가 정해지면, bfs를 사용해야한다.
- 그래서, 좌표평면에서 자주 쓰인다. 
  - **그렇지만, 좌표평면을 탐색하는 문제는 사실 순서가 중요한 것이 아니라 "그룹짓는 것"이 중요해서 어떻게 하던지 탐색을 하면 되는 경우에 속한다. 그래서, dfs로도 충분히 풀린다.**



---



#### 문제 풀이 : 그래프 탐색 vs 좌표 탐색

#### 그래프 탐색

- 정의

  - 고전적인 그래프를 탐색하는 것.

  - 즉, node / edge로 이루어져있음

- 문제 푸는 방식

  - edge가 입력으로 주어진다. 
  
  - **이것을 받아서, 그래프를 만든다**
  
    - edge를 받아서 그래프를 만든다는 사실 매우 중요하다!!
  
    - 인접행렬로 그래프를 만들면, 거기에 들어가는 값이 edge라는 말이고, 인접리스트로 그래프를 만들면, 하나의 리스트에 연결되어있는 값이 (연결된 노드, 엣지) 로 이루어져있다는 것을 생각할 수 있다!!
  
      - ```python
        # 인접리스트로 그래프 만들기
        graph = [ [] for _ in range(n+1) ] 
        ```
  
        
  
  - 그래프를 탐색한다
  
  - 새로운 class를 정의하는 경우도 있다.
  



#### 그래프 탐색 시, dfs / bfs 코드

- dfs
  - 딱 3가지만 기억하자
  - 1. (현재 노드가) 방문한 노드라면 -> return
    2. **방문하지 않은 노드라면 -> 방문 처리하기visit[True]**(이거 빼먹어서 한번 틀림)
    3. 방문하지 않는 노드라면 -> 현재 노드와 연결된 모든 노드에 대해 dfs 처리(재귀)

```python
import sys 
from collections import deque
input = sys.stdin.readline
n, m, s = map(int, input().split())
# list 안에, 간선의 갯수만큼 list 생성
board = [list(map(int, input().split())) for _ in range(m)]
# list 안에, node의 갯수만큼 list 생성
graph = [[] for _ in range(n + 1)]


def dfs(cur, vis):
    # 현재노드(cur)가,
    # 1. 방문한 node -> 종료
    if vis[cur]:
        return
    # 2. 방문 안한 node -> 출력 & 방문 & dfs
    print(cur, end=' ')
    vis[cur] = True
    for next in graph[cur]:
        dfs(next, vis)


def bfs(s):
    vis = [False] * (n + 1)
    q = deque()
    # 1. queue에 node 넣기 & 방문 표시
    q.append(s)
    vis[s] = True
    while q:
        # 2. queue에서 node 빼기 & 출력(실제 방문)
        t = q.popleft()
        print(t, end=' ')
        # 2-1. 해당 node와 연결된 nodes 탐색
        for e in graph[t]:
            # (방문했으면 건너뛰기)
            if vis[e]:
                continue
            # queue에 node 넣기 & 방문 표시
            q.append(e)
            vis[e] = True

# 1. 그래프 만들기
for i in range(m):
    graph[board[i][0]].append(board[i][1])
    graph[board[i][1]].append(board[i][0])
    
# 2. 1차원 리스트 sort()
for i in range(n + 1):
    graph[i].sort()

# param : (시작 node, visit 배열)
# param : (시작 node) 
dfs(s, [False for _ in range(n + 1)])
print()
bfs(s)
```









 #### 좌표 탐색

- 정의

  - 문제가 좌표평면에서 이루어짐
  - 즉, (y,x)로 이루어짐

- 문제 푸는 방식

  - (dfs, bfs 상관없음) 

  - **방향배열 설정**

  - 모든 방향에 대해 갈 수 있는 지 여부 확인(여기서, if 문에 들어가는 좌표는 ny, nx임을 명심. 이거 y,x로 잘못써서 엄청 틀렸다. 특히 visit[ny] [nx] 를 계속 잘못씀...)

    ```python
    for i in range(4):
            ny = y + dy[i]
            nx = x + dx[i]
                
            if (0<=ny<n) and (0<=nx<n) and not visit[ny][nx] and check_open(plain[y][x], plain[ny][nx]):
                flag = 1
                hap += dfs(ny,nx)
    ```

- **꿀팁 - 진짜 이거 개 꿀팁.... <재귀에서 리턴값으로 누적값 모으기>**

  - 만약 dfs로 좌표평면 문제를 풀 때, 한번의 dfs 탐색에서 얻어야 하는 누적값(예 - 탐색 구간의 누적합)이 필요하면 리턴 값을 활용하자!!!!!!!!!

    1. dfs 함수 내에 hap = 0 과 같은 누적값 저장 변수 선언하기

       1-1. dfs 함수 내에서, 현재 상태의 값을 변수에 할당하기

       1-2. dfs 함수 내에 dfs 함수 호출 할 때 리턴 값으로 받아오기

    2. dfs의 리턴 값으로 해당 변수 주기

    3. 실제로 dfs 함수 호출하는 부분에서 리턴값으로 받는 값이, 우리가 원하는 값임!!!!

  - 예시 코드

    - ```python
      def dfs(y,x):
          
          global flag
          # 1. 변수 선언
          hap = 0
          
          # (1. 방문한 좌표)
          if visit[y][x]:
              return
          
          # (2. 방문하지 않은 좌표)
          visit[y][x] = True
          # 1-1. 현재 상태를 변수에 할당하기
          hap += plain[y][x]
          
          y_list.append(y)
          x_list.append(x)
          
          
          for i in range(4):
              ny = y + dy[i]
              nx = x + dx[i]
                  
              if (0<=ny<n) and (0<=nx<n) and not visit[ny][nx] and check_open(plain[y][x], plain[ny][nx]):
                  flag = 1
                  # 1-2. 리턴값으로 받아오기
                  hap += dfs(ny,nx)
          
          # 2. 리턴값으로 변수 지정
          return hap
      ```

      



