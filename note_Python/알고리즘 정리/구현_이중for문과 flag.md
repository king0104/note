## 이중 for문, 그리고 flag

- 이중 for문에 flag가 사용되는 이유는, 두번째 for문이 조건 확인용 for문이기 때문이다.
  - 조건 확인용 for문

- 이를 해결하기 위해 몇가지 해결책을 살펴보자



[이중 for문과 flag 대체하기]

1. 조건에 다 때려박기

- 조건 확인용 for문에서 탐색하는 조건을, 일일히 조건에 다 적어주어야 한다

```python
plain = [[1]*4 for _ in range(10)]

full_y = []
for i in range(10):
	  #	이중 for문 사용
    is_full = True
    for j in range(4):
        if plain[i][j] == 0:
            is_full = False
            break
    
    if is_full:
        full_y.append(i)
```

```python
plain = [[1]*4 for _ in range(10)]

full_y = []
for i in range(10):
	  #	일일히 조건으로 다 적어주기
	  if plain[i][0] == 1 and plain[i][1] == 1 and plain[i][2] == 1 and plain[i][3] == 1:
        full_y.append(i)
```



2. any() 사용하기

- **flag를 사용하는 것은, 조건에 하나라도 맞지 않으면, flag를 바꿔주는 형식**일 때 사용한다.
- 이것을 위한 함수가, **any(), all()** 과 같은 함수가 있다. 이것을 이용하면 확실히 코드를 간단하게 짤 수가 있으니, 이것들을 잘 활용해보자.
