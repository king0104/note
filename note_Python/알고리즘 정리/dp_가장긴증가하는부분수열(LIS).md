## 가장 긴 증가하는 부분 수열 LIS

```python
# LIS
n = int(input())

numbers = [int(x) for x in input().split()]
max_len = [1] * n # DP배열 max_len

for i in range(1, n):
    for j in range(i): # 현재 좌표
        if numbers[j] < numbers[i]: # 현재보다 앞선 좌표 체크
            max_len[i] = max(max_len[i], max_len[j] + 1)


print(max(max_len))
```

