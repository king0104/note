### 입력받은 값으로 deq 만들기

- 오류
- 다음과 같이 = 를 사용하여 할당하면, 정수 그 자체가 deq가 되버린다! 'int' object is not subscriptable 이런 오류가 뜨면 의심해보자.

```python
    deq = deque()
    if deq_size == 1:
        deq = int(input())
    else:
        deq = map(int,input().split())
```

- 정상

- **deq.append**를 사용해, 값을 하나씩 넣어주기.
- appendleft 하면, queue 처럼 넣는 것이다. 일반적으로는 list 형태로 처음 넣은 값이 맨 앞에 위치하도록 하기 때문에, append를 사용하자.

```python
    deq = deque()
    if deq_size == 1:
        deq.append(int(input()))
    else:
        for a in map(int,input().split()):
            deq.append(a)
```



- 정상 2
- deq = input()
- deq에 string이 들어가면, 알아서 원소 하나하나씩 분리해서 deq에 저장해준다

```python
deq = input()
```

