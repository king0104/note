### dictionary

- 순서 있음(iterable 객체임)
- { "key" : value }
  - {"a" : 1, "b" : 3}
  - key 중복 불가능, value 중복 가능
  - key로 접근한다



- **key 값으로 튜플 가능**. 리스트 불가능
  - key값을 **2차원**으로 설정하고 싶을 때 유용하다 (**좌표**를 키값으로 설정할 때)



#### 관련 함수

- keys(), values(), items()
- get(), clear()
- in 연산자 - key값으로 적용



<입력 받았을 때, 존재하지 않으면 -> key,value 추가 / 존재하면 -> value 추가 하기>

- get() 사용 -> None 인지 아닌지로 구별

- ```python
  if dict.get(name) == None:
      dict[name] = 1
  else:
      dict[name] += 1
  ```

  

https://yaneodoo2.tistory.com/entry/%EC%BD%94%EB%94%A9%ED%85%8C%EC%8A%A4%ED%8A%B8%EB%A5%BC-%EC%9C%84%ED%95%9C-%EB%94%95%EC%85%94%EB%84%88%EB%A6%AC-dictionary-%EC%9E%90%EB%A3%8C%ED%98%95-keys-values-get-in-items

#### 정렬

- sorted()를 사용해야 한다(리스트가 아니므로)

- **dict.items()** 를 사용해야함

  - dict로 정렬하면, key값만 정렬된 값이 리턴됨

  

![image-20220724115804846](/Users/yoon/Library/Application Support/typora-user-images/image-20220724115804846.png)

https://rfriend.tistory.com/473





[딕셔너리 기본 사용법 총정리 사이트]

https://wikidocs.net/16#key-value