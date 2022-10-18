## ₩DFS의 코드 부분 나눠보기

- dfs는

  1. (현재 상태를 보여주는 파라미터로) dfs 함수가 수행하는 작업을 표현하는 부분,

  2. 다음으로 넘어가는 코드 부분

  두 가지가 존재한다고 생각하면 편하다



- 10971_외판원순회2


```python
import sys
sys.setrecursionlimit(10 ** 5)


n = int(input())
matrix = [list(map(int,input().split())) for _ in range(n)]

visit = [False]*(n+1)
start = 1
cost = 0
cost_list = []
cnt = 0
def dfs(s):
    global start
    global cost
    global cnt

		# 1. dfs의 실제 로직이 들어가는 부분
    # - 현재 파라미터를 이용해 작성한다
    # - dfs란 무엇을 하는 함수인지 여기서 표현한다
    visit[s] = True
    
   	# 2. dfs에서, 다음으로 넘어가는 부분
    for next in range(n):
        if matrix[s][next] != 0 and not visit[next]:
            cnt += 1
            cost += matrix[s][next]
            dfs(next)
            ###################################
            # 백트래킹 시, 돌아오는 부분
            cnt -= 1
            visit[next] = False
            cost -= matrix[s][next]

        if matrix[s][next] != 0 and cnt == n-1 and next == start:
            cost += matrix[s][next]
            cost_list.append(cost)
            cost -= matrix[s][next]


dfs(start)
print(min(cost_list))
```



- 재귀함수의 특성상, 종료조건이 있는 것이 더 일반적이라고 생각한다.
- 따라서, if visit[s]와 같은 것은 써주고, 다음으로 넘어가는 부분에서 not visit[] [] 이 부분을 고려해볼 필요가 있을 듯 하다.
