#### 기본 예시

```
def calcGugudan(dan):
    for i in [1,2,3,4,5,6,7,8,9] :
        print(dan, " * ", i, " = ", dan * i)
```

---

#### range()

(a) `range(limit)`: `0`에서 `limit - 1`까지를, `1씩 증가하는 형태의` 값으로 돌려 줍니다.

(b) `range(start, end)`: `start`에서 `end`까지를, `1씩 증가하는 형태의` 값으로 돌려 줍니다.

(c) `range(start, end, step)`: `start`에서 `end`까지의 값을 돌려 주는데, 숫자의 증가폭을 `step`만큼으로 합니다

- 예시

```python
print("Case.1")
for i in range(3) :
    print(i)

print("Case.2")
for i in range(1,3) :
    print(i) 

print("Case.3")
for i in range(0,10,2) :
    print(i)   

print("Case.4")
for i in range(10,0,-2) :
    print(i) 
```



---

