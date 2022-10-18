### list comprehension

**리스트를 쉽게, 짧게 한 줄로 만들 수 있는 파이썬의 문법**

보통 배열을 만들고 사용할 때는 선언과 할당을 같이 하고, 선언만 하거나 할당만 하는 경우는 없기 때문에 이 작업을 간편하게 한 줄로 해결하는 것이 리스트 컴프리헨션이다.

```
[ ( 변수를 활용한 값 ) for ( 사용할 변수 이름 ) in ( 순회할 수 있는 값 )]
```

이 문법은 앞선 예제의 파이썬 버전과 비교해보면 좀 더 쉽게 이해할 수 있다. **배열을 만들고 for 반복문 안에서 각 원소의 값을 할당하는 작업이 이 한 줄로 일어난다.** 괄호 안의 이름들을 조금 설명해보겠다.



https://shoark7.github.io/programming/python/about-list-comprehension-python#3a



#### 예제

```python
c = 'long long'.split()
nlist = [d[::-1] for d in c]
print(nlist)

# 결과
# ['gnol', 'gnol']
```

