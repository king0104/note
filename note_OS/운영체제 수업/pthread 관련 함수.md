### pthread



#### pthread_create()

- ```c
  int pthread_create(pthread_t *thread, const pthread_attr_t *attr, void *(*start_routine)(void *), void *arg)
  ```

쓰레드를 생성합니다 

첫번째 매개변수인 **thread** 는 쓰레드가 성공적으로 생성되었을때 생성된 쓰레드를 식별하기 위해서 사용되는 쓰레드 식별자이다. 

두번째 매개변수인 **attr** 은 쓰레드 특성을 지정하기 위해서 사용하며, 기본 쓰레드 특성을 이용하고자 할경우에 NULL 을 사용한다. 

세번째 매개변수인 **start_routine**는 분기시켜서 실행할 쓰레드 함수이며, 

네번째 매개변수인 **arg**는 위 start_routine 쓰레드 함수의 매개변수로 넘겨집니다.



#### pthread_join()

- ```c
  int pthread_join(pthread_t th, void **thread_return);
  ```

  th라는 특정 쓰레드가 종료하기를 기다렸다가, 쓰레드가 종료된 이후 다음 진행

  

  첫번째 매개변수 **th** 는 기다릴 쓰레드의 식별자.

  두번째 매개변수 **thread_return** 은 쓰레드의 리턴값.  thread_return 이 NULL이 아닌 경우 해당 포인터로 쓰레드의 리턴 값을 받아올수 있습니다.  

  join된 쓰레드 (종료된 쓰레드)는 모든 자원을 반납하게 됩니다. 

  

  리턴값: 성공하면 0,  실패하면 에러코드 리턴

  