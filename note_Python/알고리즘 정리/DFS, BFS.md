### 개념 : DFS or BFS

- 문제에 적용할 때, 아무거나 적용해도 되는 경우가 대부분. 어떻게 하던지 탐색을 하는 경우라면, 둘 다 사용할 수 있다. 여기서, 조금 나누자면 다음과 같다.



- 코드에서, 기본적으로 **"그래프를 그린다"** 라는 생각은 해보는 것이 좋다. 결국 그래프를 탐색하는 것이기 때문에, **문제의 어떤 부분이  어떻게 그래프로 그려질 지** 아는 것이 모든 문제의 기본!!!!!!

  - 예시1 - 좌표평면 : 좌표평면이 주어진 것은, 이미 그래프가 주어진 것이다. 그래프를 그릴 필요가 없음!

  

- **최단 거리를 구하는 문제는 반드시 BFS로 풀어야 하며**, DFS를 하면서 메모이제이션을 하는 방식은 상태간의 선후 관계가 없기 때문에 정답을 보장할 수 없습니다. 현재 데이터가 약해서 이 코드도 통과가 되지만, 저격 데이터를 만들 수 있음을 확신합니다.

  - 그래서, **좌표평면이** 나오고, **어디서 어디로 가는 비용** 구하라 하면 **무조건 bfs**로 풀자.


#### dfs

- 어떻게 하던지 간에 탐색을 하면 되는 경우

- 팁)
  - pypy3로 메모리 초과난다 -> sys.setrecursionlimit(10**5) 로 바꾸기

#### bfs

- **탐색에 순서가 있는 경우**. 한 칸 다음 다음 3칸 탐색 이런식으로 순서가 정해지면, bfs를 사용해야한다.



- **가중치가 동일한 경우(중요!!!).** 이 경우에는, 출발 노드에서 다른 노드로 가는 최단거리(최소비용)을 bfs로 계산할 수 있기 때문에, 문제에서 자주 쓰인다.
  - **가중치가 동일하다면, 출발 노드에서 다른 노드로 가는 최단거리(최소비용)를 구할 수 있다.**
  - bfs로 탐색하는 순서가 큐에 들어가는 순서인데, 그 순서가 최소비용 순으로 들어가기 때문이다(? 이 문장은 애매하니까 문제 풀면서 다듬어보기)




- **좌표평면에서, 최단거리**를 묻는 경우
  
  
  - 좌표평면은 **한 좌표에서 다른 좌표로 가는 가중치가 동일**하기 때문에  bfs를 쓰게 된다!!!
  
  
  - 그렇지만, **좌표평면을 탐색하는 문제 중"그룹짓는 것"**이 중요한 문제에 대해서는, 어떻게 하던지 탐색을 하면 되는 경우에 속한다. 이땐 dfs나 bfs나 같은 결과를 가져온다.



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

- 기본적으로 코드 구성은 딱 2가지이다. 그래프 그린다는 생각을 머릿속에 박자!
  1. **그래프를 그리기**
  2. **알고리즘 (dfs, bfs) 작성하기**



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


---

---

### 꿀팁1) dfs(재귀), bfs(큐)에서 값 주고받는 방법 2가지

- 매개변수로 넘기는 것 : top down 방식으로, **마지막 함수에서 결과값 얻기** 가능

  - 주로 bfs에서 사용하는 방법

  - 출발 노드에서 다른 노드로 가는 최소비용을 계산한다. 그때, bottom부터 top으로 갈 때 최소비용이 1씩 증가하는 것을 표현하기 위해 매개변수에 +1씩 해주어 값을 넘기게 된다.

  - ```python
    def bfs(start):
        
        q = deque()
        q.append((start,0))
        
        while q:
            t = q.popleft()
    
            if t[0] == b:
                return t[1]
            
            for next_node in [t[0]*2, int(str(t[0]) + '1') ]:
                
                if 0<= next_node <= INF:
                    q.append((next_node,t[1]+1)) #매개변수로 값 넘기기 - bottom up이다.
                    
        return -1
    ```

    

  

- 리턴값으로 얻어오는 것 : bottom up으로, 마지막까지 갔다가 다시 올라오면서 결과가 쌓이므로, **재귀의 첫번째 함수에서 결과값을 얻을 수 있음**. **즉, 모든 dfs에서 나오는 결과의 합을 구할 때 유용**

  - 주로 dfs에서 사용하는 방법

  - 그래프의 모든 노드에 대해 어떤 결과를 도출할 때 사용

  - ```python
    # 그래프의 모든 노드에 대해, 어떤 결과를 도출해낸다(return값으로)
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




----



### 꿀팁2) bfs와 dp의 차이

- 백준 16928 뱀과 사다리 게임
- 처음에 접근을 dp로 했는데, 잘못된 접근이였다. 나와 같은 고민의 답변을 가져왔다.
  - https://www.acmicpc.net/board/view/80099 : 해당 문제를 dp로 풀 수 없는 이유
  - 말로는 설명하기 어려웠는데, 확실히 **사이클이 생기지 않는** 그래프/단방향에서 DP를 사용하기 편할 것 같네요. 



