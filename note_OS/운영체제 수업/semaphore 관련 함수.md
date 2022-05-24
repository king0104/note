## SP 관련 용어

#### 타입

- sem_t
  - 세마포어 구조체를 말한다.
  - value, 





#### 함수

- sem_init

Unnamed 세마포어는 sem_open 호출이 필요하지 않다. 대신에 아래의 2가지 호출이 필요하다.

```
{
  sem_t semid;
  int sem_init(sem_t *sem, int pshared, unsigned  value);
}
```

**pshared**
이 인자는 임의의 프로세스의 쓰레들 사이에 혹은 프로세스들 사이에 세마포어가 공유되는지 어떤지를 표시한다. 만약 pshared 값이 0이라면 세마포어는 프로세스의 쓰레드들 간에 공유된다. Pshared가 0이 아니면 세마포어는 프로세스 간에 공유된다.
**value**
초기화될 때 세마포어가 가지는 값
세마포어가 초기화 되자마자 프로그래머는 sem_t 타입의 세마포어를 사용할 수 있다. 세마포어에 대한 lock과 unlock 동작은 앞서 본 바와 같이 sem_wait(sem_t *sem)와 sem_post(sem_t *sem)을 통해 이루어 진다.