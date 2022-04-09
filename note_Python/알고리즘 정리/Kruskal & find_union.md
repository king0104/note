### Kruskal algorithm

- 최소 신장 트리를 만드는 알고리즘
- 최소 신장 트리?
  - 그래프에서, 최소 비용으로 모든 노드를 연결하는 것을 말한다
  - **사이클이 없어야 한다 -> find_union 알고리즘 사용**



1. 그래프의 간선에 대해 오름차순으로 정렬한다

2. 비용이 가장 작은 간선부터 선택하면서,

   1. 양쪽 노드의 부모 노드가 같은지 확인한다 - find() 함수 사용

      - 같으면 : 해당 간선 무시
      - 다르면 : 해당 간선 선택(= 최소 신장 트리에 넣기) & union() (= 같은 부모 노드로 업데이트)

      

[백준 1197_최소스패닝트리]

```python
# by kruskal
from collections import deque

v,e = map(int,input().split())

edges = [ list(map(int,input().split())) for _ in range(e) ]

# < 초기화 >
# 루트노드 저장 배열 초기화
parent = [0]*(v+1)
for i in range(v+1):
    parent[i] = i 

# < 이용하는 함수 >
# 1. 루트노드 찾기 = 집합 지정하기
def find(u):
    if u != parent[u]:
        parent[u] = find(parent[u])
    return parent[u]

# 2. 두개의 집합을 하나로 만들기
def union(a,b):
    rootA = find(a)
    rootB = find(b)
    parent[rootA] = rootB


# < 크루스칼 알고리즘 >
# 1. 최소비용으로 정렬하기
edges.sort(key=lambda x:x[2])
q = deque(edges)


# 2. 최소신장트리 만들기
tree = []
while len(tree) < v-1:
     
    edge = q.popleft()
        
    a,b,cost = edge[0], edge[1], edge[2]
    
    if find(a) != find(b):
        union(a,b)
        tree.append(edge)

ans = 0   
for t in tree:
    ans += t[2]

print(ans)
```



---



### find_union

#### 0. parent 배열 초기화

- 맨 처음엔, "자신의 부모노드는 자신"이다!!

```python
# < 초기화 >
# 루트노드 저장 배열 초기화
parent = [0]*(v+1)
for i in range(v+1):
    parent[i] = i 
```



#### 1. find()

```python
# 1. 루트노드 찾기 (= 집합 지정하기)
def find(u):
    if u != parent[u]:
        parent[u] = find(parent[u])
    return parent[u]
```



#### 2. union()

```python
# 2. 두개의 집합을 하나로 만들기
def union(a,b):
    rootA = find(a)
    rootB = find(b)
    parent[rootA] = rootB
```

