### dictionary

- 순서가 없다
- { "key" : value }
  - {"a" : 1, "b" : 3}
  - key 중복 불가능, value 중복 가능
  - key로 접근한다



#### 관련 함수

- keys(), values()
- items()
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

![image-20220724115804846](/Users/yoon/Library/Application Support/typora-user-images/image-20220724115804846.png)

https://rfriend.tistory.com/473