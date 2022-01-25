
### 역순

#### 1. range(n-1,-1,-1)

- step을 -1로 주면, 역순이 된다.

- **0~n-1 까지의 범위를 지정하고 싶다면,  start, stop을 0,n 이 아니라 n-1,-1 로 지정해줘야 함을 유의하자.**

  - ```python
    for i in range(n-1,-1,-1):
    ```

- 2022.1.6 이걸로 한번 더 틀림... n-1부터 -1까지 해주어야 한다는 것 잊지말자.... start는 포함이고 end는 미포함이다!!!!!!!!!!!!!



#### 2. reversed(range())

- 참고로 reversed(range()) 가 있는데, 이건 iterator를 리턴하기 때문에 그냥 무조건 range(n-1,-1,-1)으로 사용하자. - iterator는 한번 사용하면 사라지기 때문(포인터라서)
- 꼭 reversed(range()) 사용하고 싶으면, list(reversed(range())) 를 사용해 iterator로 객체를 만들어주어야 한다.