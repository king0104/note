## BFS

기본적으로 최단거리나 최소비용, 최소시간 + 좌표평면이면 무조건 BFS임.







### BFS 코드 분석 - 이것만 제대로 알면 문제 풀기 쉽다!!

#### <간단 설명>

1. **큐에 들어간 노드 = 방문할 수 있는 노드**
   - 생각해보면, BFS에서 가장 먼저 하는 작업이다. 시작 노드인 첫번째 노드를 큐에 넣고 방문 처리를 한다. 그래서 1번으로 생각하면 쉽겠다.
2. **큐에서 뽑은 노드 = 현재 방문 중인 노드**
   - 첫번째 노드를 큐에 넣었으면, 그 다음 바로 큐에서 노드 하나를 뺀다.
   - 방문할 수 있는 노드이기에 큐에 들어간 첫번째 노드를 뽑아 현재 방문 중인 노드로 생각하고, 작업이 이루어진다.
3. 1번과 2번이 번갈아 작동하며, BFS 탐색이 이루어진다.



---

#### <자세한 설명>

#### 1. 큐에 들어간 노드 = 방문할 수 있는 노드

- **큐에 들어간 노드 = 방문할 수 있는 노드( 현재(뽑은 노드) 기준 다음 노드들 )**

  - 실제로 코드로 짤 때, **현재 노드(=뽑은 노드) 기준 다음 번에 방문 가능한 노드를 큐에 넣는 작업**을 하기 때문에 이렇게 말하는 것이다.

  - 생각해보면, BFS에서 가장 먼저 하는 작업이다. 시작 노드인 첫번째 노드를 큐에 넣고 방문 처리를 한다. 그래서 1번으로 생각하면 쉽겠다.
  
    - ```python
      # 예시1
      
      # 주사위 한번 굴리기
      # 현재 노드에서 갈 수 있는 노드들 그래프로 그리기
      graph = []
      for i in range(1,7):
      	if 1 <= (t[0]+i) <= 100:
      	graph.append( t[0]+i )
      
      # 방문 가능한 노드(현재 기준 다음 노드들)를 큐에 넣는 작업
      for next_node in graph:
      
      	if visit[next_node] == False:
      
      	if ls[next_node]:
      		q.append((ls[next_node][0],t[1]+1))
      		visit[ls[next_node][0]] = True
      
      
      	else:
      		q.append((next_node,t[1]+1))
    		visit[next_node] = True
      ```
  
    - ```python
      # 예시2
      for i in range(4):
          # 한 칸 이동
          ny = t[1] + dy[i]
          nx = t[2] + dx[i]
          nsize = t[3] # 먹은게 아니니까, size 그대로
          ntime = t[0]+1 # 시간 증가
          ncnt = t[4] # 먹은게 아니니까, 먹은 횟수 cnt 그대로
      
      # 방문 가능한 노드를(현재 기준 다음 노드들) 큐에 넣는 작업
      if 0<=ny<n and 0<=nx<n and not visit[ny][nx] and plain[ny][nx] <= t[3]:
          heapq.heappush(q,[ntime,ny,nx,nsize,ncnt])
        visit[ny][nx] = True
      ```

      

  - visit 배열 처리는 큐에 넣을 때 같이 해준다.

  - 이때 실제로 방문했다고 생각하고 작업을 진행하는 것은 아님. 뽑았을 때 실제로 방문했다고 생각하고 작업함. 아래의 설명 참조

  


#### 2. 큐에서 뺀 노드 = 현재 방문 중인 노드

- 그렇다면, **큐에서 뺀 노드 = 방문할 수 있는 노드(다음 노드)를 현재 방문하고 있다는 것(방문할 수 있는 노드에 대해 현재 작업하고 있다는 것) = 현재 방문 중인 노드**이다.

  - 그러니까, 큐에서 뺀 노드에 대한 작업은, 좌표평면으로 생각하면 다음 4노드에 대한 작업을 진행하고 있는 것이라고 생각하면 된다.

  - **큐에서 뺀 노드 = 방문할 수 있는 노드를 현재 방문하고 있다는 것 = 현재 방문 중인 노드** 로 생각하고 작업을 진행해야 하는 이유가 또 있다. 구현에서, 우리는 "어떤 상태를 확인하는 코드 구간"은 가장 위에 위치해야한다고 말했다. 왜냐하면, 첫번째 값도 상태를 확인해야 하기 때문이다. 큐에서 뺀 노드는 BFS의 시작 노드부터 시작하게 되므로, 이러한 조건과도 일치한다. 그래서, **큐에서 뺀 노드를 현재 방문한 노드**라고 생각하고 BFS를 접근해야한다.

  - 첫번째 노드를 큐에 넣었으면, 그 다음 큐에서 노드 하나를 빼고 작업을 한다. 즉, 첫번째 노드를 현재 방문중이라는 것이다. 여기에 대해 작업이 이루어지고, 다시 1,2번이 번걸아 일어나는 것이다./

    - ```python
      # 예시
      while q: 
      	# 큐에 들어간 노드 = 방문할 수 있는 노드
      	# 즉, 큐에서 뺐다는 건, 방문할 수 있는 노드를 현재 방문하고 있다는 것.
      	t = heapq.heappop(q)
      
      	# 물고기 만났을 때 - 물고기 먹고, cnt 증가 -> 아기상어 크기 업 여부 확인
      	if plain[t[1]][t[2]] not in [0,9] and plain[t[1]][t[2]] < t[3]:
      
      		plain[t[1]][t[2]] = 0 # 물고기 먹음 -> 해당 칸 0으로 됨
      
      	# print(t[0], (t[1],t[2]))
      
      		t[4] += 1 # cnt 증가
      
      		if t[3] == t[4]:
      		t[3] += 1 # 아기상어 크기 업
      		t[4] = 0 # 카운트 값 0으로 만들기
      
      		ans = max(ans,t[0])
      
              visit = [ [False]*n for _ in range(n) ]
      		visit[t[1]][t[2]] = True
      		q = []
      ```

      


  

  







#### bfs 예시 코드1 - 16236 아기상어

```python
ans = 0
def find_shortestfish(time,sy,sx,size,cnt):
    
    # time,sy,sx,size,cnt # 4빼고 다 바꾸기
    
    global ans
    
    visit = [ [False]*n for _ in range(n) ]
    
    q = []
    heapq.heappush(q,[time,sy,sx,size,cnt])
    visit[sy][sx] = True
    
    while q: 
        # 큐에 들어간 노드 = 방문할 수 있는 노드
        # 즉, 큐에서 뺐다는 건, 방문할 수 있는 노드를 현재 방문하고 있다는 것.
        t = heapq.heappop(q)
        
        # 물고기 만났을 때 - 물고기 먹고, cnt 증가 -> 아기상어 크기 업 여부 확인
        if plain[t[1]][t[2]] not in [0,9] and plain[t[1]][t[2]] < t[3]:
            
            plain[t[1]][t[2]] = 0 # 물고기 먹음 -> 해당 칸 0으로 됨
            
            # print(t[0], (t[1],t[2]))
            
            t[4] += 1 # cnt 증가
            
            if t[3] == t[4]:
                t[3] += 1 # 아기상어 크기 업
                t[4] = 0 # 카운트 값 0으로 만들기
            
            ans = max(ans,t[0])
            
            visit = [ [False]*n for _ in range(n) ]
            visit[t[1]][t[2]] = True
            q = []
            
            
        
        for i in range(4):
            # 한 칸 이동
            ny = t[1] + dy[i]
            nx = t[2] + dx[i]
            nsize = t[3] # 먹은게 아니니까, size 그대로
            ntime = t[0]+1 # 시간 증가
            ncnt = t[4] # 먹은게 아니니까, 먹은 횟수 cnt 그대로
            
            if 0<=ny<n and 0<=nx<n and not visit[ny][nx] and plain[ny][nx] <= t[3]:
                heapq.heappush(q,[ntime,ny,nx,nsize,ncnt])
                visit[ny][nx] = True
```

