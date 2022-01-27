### Thread 구현 & 실행

- 쓰레드를 구현한다는 것 : "쓰레드를 통해 작업하고자 하는 내용으로 run()의 몸통을 채우는 것" 일 뿐이다!!

---

#### 구현

- 결국, **쓰레드 객체를 만들고 -> start()** 를 해주면 쓰레드 실행됨.
- 쓰레드 객체를 만드는 방식이 2가지 있는 것
  1. with new Thread
  2. with new Runnable

---

#### 1. Thread 클래스 상속

1. Thread 를 상속받는 클래스 생성

   ```java
   class ThreadEx extends Thread {
   	public void run() {
   	
   	}
   }
   ```

2. new ThreadEx() - **쓰레드 객체 생성**

   ```java
   ThreadEx t1 = new ThreadEx();
   ```

3.  쓰레드 객체.start()

   ```java
   t1.start()
   ```

   

#### 2. Runnable 인터페이스 구현

1. Runnable 인터페이스를 구현하는 클래스 생성

   ```java
   class ThreadEx implements Runnable {
   	public void run() {
   	
   	}
   }
   ```

2. Runnable r = new ThreadEx()

3. Thread t2 = new Thread(r) - **쓰레드 객체 생성(with Runnable)**

   ```java
   Runnable r = new ThreadEx();
   ```

4.  t2.start()

   ```java
   t2.start()
   ```

   