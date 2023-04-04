### any(iterable)

- any(iterable)
  - iterable 원소 중 하나라도 True가 있으면 True
  - 즉, **list comprehension의 원소들이 bool**이어야 한다



결국 for문 한줄 출력은, list comprehension이다!

```python
# 올바른 예시
# list comprehension의 원소들이 bool이어야 한다!
any( i>5 for i in range(10) )

# 올바르지 않은 예시
# list comprehension의 원소들이 bool이 아니라, 그냥 숫자임
any( i for i in range(10) if i>5) 
any( [i for i in range(10) if i>5] ) 
```

