## BufferedReader에서 read, readline 차이

- read()

  - 하나의 문자를 읽는 것.

  - ```java
    StringTokenizer st = new StringTokenizer(br.read());
    // 이렇게 사용 불가능.
    // string이 아니라 문자 하나만 읽기 때문이다!!!
    ```

  - read()는 개행문자를 읽어들이지 않는다
  - read()가 읽어들이는 값은, **아스키코드 값**임을 명심!!

  

- readLine()

  - 한 줄을 읽는 것.

  - ```java
    StringTokenizer st = new StringTokenizer(br.readLine());
    // 이렇게 사용 가능
    // 한 줄을 읽어서 st라는 객체에 전달.
    
    intArray[i] = Integer.parseInt(st.nextToken());
    // st.nextToken() 사용하여 한 문자씩 끊어서 사용
    
    ```



- 한 줄에 여러 문자를 입력받을 때 vs  여러 줄에 문자 입력받을 때

  - 한 줄에 여러문자

    - ```java
      BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
      intArray[i] = Integer.parseInt(st.nextToken());
      ```

  

  - 여러줄로 문자 여러개

    - **for 문에 StringTokenizer st = new StringTokenizer(br.readLine()) 넣어서 여러줄로 받기**

    - ```java
      BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
      
      int intArray[] = new int[5];
      int max = 0;
      
      for(int i=0;i<5;i++){
          StringTokenizer st = new StringTokenizer(br.readLine());
          intArray[i] = Integer.parseInt(st.nextToken());
      ```

---

아래의 팁 : 2021.7.6 최신버전

### *tip*

- abcd1234 와 같은 문자열 입력받기 :  String str = br.readLine();

- 2 와 같은 정수 하나 입력받기 : int n = Integer.parseInt(br.readLine());

- **한 줄에 띄어쓰기로 여러개 입력받기** : StringTokenizer 사용

  - ```java
    StringTokenizer st = new StringTokenizer(br.readLine());
    while(st.hasNextToken()){
    	array[i] = st.nextToken();
    }
    
    ```

  - array의 타입은 문자열을 받는지, 문자를 받는지, 정수를 받는지에 따라 달라진다

  - st.nextToken이 반환하는 값은 String이므로, 다른 타입으로 바꾸려면 형변환을 해야 한다

  - 

- 위에서 말한 한줄을 여러개 입력받는 경우

  - 위의 코드를 반복해서 사용하면 된다. readLine()이 한줄을 말하는 것이기 때문!

  - 반복할 때 방법

    - **br.readLine()을 반복시키면 된다.**

    1. for문에 StringTokenizer st = new StringTokenizer(br.readLine()); 넣기
    2. 직접 StringTokenizer st = new StringTokenizer(br.readLine());를 여러번 치기
