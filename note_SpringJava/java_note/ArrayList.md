### ArrayList

- 인덱스를 가지는 배열이다.
- 그래서, **인덱스로 배열의 값들을 조정하는 것**임을 명심!





### 메서드

1. 깊은 복사

- ```
  b.addAll(a);
  c.addAll(a);
  ```

2.  정렬 : 오름차순 / 내림차순

- ```
  Collections.sort(b);
  Collections.sort(c,Collections.reverseOrder());
  ```

3. ArrayList의 크기

- ```
  a.size()
  ```



### 의문점

- 이걸 쓰는 경우가 언제인가???
- 크기 모르는 경우에만 쓰는건가??
- 나머지는 배열이 편한 느낌이긴 함.
