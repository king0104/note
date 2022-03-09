#### 카프카 동작 방식

1. Zookeeper 와 Kafka서버를 띄우고

2. 서버에 Topic을 생성

3. Consumer로 생성한 Topic을 구독

4. Producer로 생성한 Topic에 메세지 전달

5. Consumer는 구독중이던 Topic에 메세지가 있는 걸 확인하고 읽어서 출력한다.



출처: https://debaeloper.tistory.com/24 

---

https://victorydntmd.tistory.com/344



#### broker

- 대신해주는 아이
- producer, consumer가 카프카를 사용할 때, 브로커를 거치게 된다.
  - 카프카에 프로듀싱 해줘
  - 카프카에서 컨슈밍 해줘



#### topic



- 컨슈머가 느린 이유

컨슈머를 늘려야한다 -> 컨슈머를 하는 쓰레드를 늘려야한다.
