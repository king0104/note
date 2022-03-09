### 쓰레드

- **하나의 작업 단위!!!**
  - 쓰레드로 정해둔 클래스에, run() 이라는 메서드를 정의한다.
  - 그 안에 내가 원하는 작업을 작성하면 끝.



### 멀티쓰레드

##### ExecutorService

- 멀티스레드 프로그래밍 시 편하게 해줌.

< 기본 코드 작성 요령 >

1. ExecutorService를 쓰레드 풀 갯수와 함께 정의하기

   - ```java
     ExecutorService executor = Executors.newFixedThreadPool(4);
     ```

2. Worker 클래스(실제로 작업 진행할 클래스) 작성하기

   - Runnable 혹은 Callable을 implement 한다.

   - ```java
     @NoArgsConstructor
     @AllArgsConstructor
     class Worker implements Runnable {
     
         public void run(){
             try{
     
             catch(Exception e) {
                 e.printStackTrace();
             }
         }
     }
     ```

3. ExecutorService를 사용하는 메인 클래스에서 worker 생성하기

   - ```
     Worker worker = new Worker();
     ```

4. ExecutorService에 Worker를 submit한다

   - ```java
     executor.submit(worker);
     ```



참고 블로그

- https://codechacha.com/ko/java-executors/
- https://gompangs.tistory.com/entry/JAVA-ExecutorService-%EA%B4%80%EB%A0%A8-%EA%B3%B5%EB%B6%80