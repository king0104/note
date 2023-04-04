### Kruskal algorithm

- 최소 신장 트리를 만드는 알고리즘
- 최소 신장 트리?
  - 그래프에서, 최소 비용으로 모든 노드를 연결하는 것을 말한다
  - **사이클이 없어야 한다 -> find_union 알고리즘 사용**

---

### 핵심

최소 신장 트리를 만들기 위해선, 간단한다.

그냥, **"가장 작은 간선부터 하나씩 graph(tree)에 추가해주면 끝이다!!"**

---

구체적인 과정은 다음과 같다.

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

edges = []
for _ in range(m):
    a, b, d = map(int, input().split())
edges.sort(key=lambda x: x[2]) # edge 정렬

# < 초기화 >
# 루트노드 저장 배열 초기화
parent = [i for i in range(v + 1)]

# < 이용하는 함수 >
# 1. 루트노드 찾기 = 집합 지정하기
def find(a): #( find는 루트 노드를 찾는 함수임)
    if parent[a] == a:
        return a

    parent[a] = parent(root[a]) # 최상위 부모노드로 업데이트하기
    return parent[a]
  
# 2. 두개의 집합을 하나로 만들기
def union(a,b):
    rootA = find(a)
    rootB = find(b)
    parent[rootA] = rootB


# < 크루스칼 알고리즘 >
graph = []
ans = 0
for a, b, d in edges:

    if find(a) != find(b):
        graph.append([a, b, d])
        ans += d
        union(a, b)

# mst를 만든 경우 (간선이 n-1개)
if len(graph) == n-1:
    print(ans)
    
# mst를 못만든 경우 (간선 n-1보다 작음)
else:
    print(-1)
```



---



### find_union

#### 0. parent 배열 초기화

- 맨 처음엔, "자신의 부모노드는 자신"이다!!

```python
# < 초기화 >
# 루트노드 저장 배열 초기화
parent = [i for i in range(v + 1)]
```



#### 1. find()

```python
# 1. 루트노드 찾기 (= 집합 지정하기)
def find(a):
	if parent[a] == a:
		return a
	parent[a] = find(parent[a])
  
	return parent[a]
```



#### 2. union()

```python
# 2. 두개의 집합을 하나로 만들기
def union(a,b):
    rootA = find(a)
    rootB = find(b)
    parent[rootA] = rootB
```



---

### 경로압축

(1) 경로압축은 find 함수에서 최상위 부모를 찾을 때마다, 부모를 이 때 찾은 최상위 부모로 업데이트하는 방식입니다. 이렇게 하면 나중에 동일한 값의 최상위 부모를 찾을 때, 시간이 엄청나게 절약됩니다.

```python
def find(a):
	if parent[a] == a:
		return a
	parent[a] = find(parent[a])
  
	return parent[a]
```



경로압축을 한다는 건, 그래프 상에서 부모 노드를 실제로 바꾸는 것임을 알아야 한다. root = [1,2,3,3]에서

root = [3,3,3,3]으로 바뀌었다는 것은, 그래프가 아래와 같은 그림으로 변했다는 것을 의미한다.

![image-20230226144727141](/Users/yoon/Library/Application Support/typora-user-images/image-20230226144727141.png)





### 분리집합

- **그래프 여러개에 대해서, 그룹을 구분짓는 것**을 말한다.
- find()를 하면, 한 노드의 최상위 노드를 알 수 있기 때문에, find()해서 나오는 최상위 노드로 그룹을 구분한다.
  - **find()해서 나오는 노드가 같으면, 같은 그룹. 아니면, 다른 그룹!**



참고블로그

- https://4legs-study.tistory.com/94



### union find로 그래프 만들 때 주의점

- union find의  root 배열으로 그래프를 만들 수 있다. root 리스트를 하나씩 탐색하면서 graph에 넣어주면 된다.

- 주의점 1 :

  - 단순히 현재노드에 부모 노드를 연결해주는 작업만 하면 단방향그래프가 된다는 점이다. dfs, bfs할 때 거의 다 양방향 그래프를 사용하므로, 부모노드에서 현재노드를 연결해주는 작업도 해주어야 한다.

- 주의점 2 :

  - 자기 자신을 부모 노드로 갖는, 최상위노드는, 그래프 만들때 제외해주기

- 예시코드

  - 

  - ```python
    graph = [[] for _ in range(n+1)]
    for i in range(1,n+1):
        if i != root[i]: # 자기 자신을 부모 노드로 갖는 노드는 제외하기(최상위노드)
            graph[i].append(root[i]) # 1. 현재 노드에 부모 노드 연결하기
            graph[root[i]].append(i) # 2. 부모 노드에 현재 노드 연결하기
    ```
