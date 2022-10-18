## input()

- Input()은, 우리가 입력하는 문자에다가, 줄바꿈 문자(엔터. 즉, '\n')까지 받게 된다

  - ```python
    name = input()
    
    if dict.get(name) == None:
    	dict[name] = 1
    else:
    	dict[name] += 1
    ```

    

  - 위의 코드에, a 를 입력했을 때의 결과

  - ![image-20220724120936926](/Users/yoon/Library/Application Support/typora-user-images/image-20220724120936926.png)

- 그래서, 우리가 입력한 문자열만 받고 싶다면, rstrip() 을 이용하면 된다!!

