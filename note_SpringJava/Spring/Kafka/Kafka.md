## 카프카 동작 방식

1. Zookeeper 와 Kafka서버를 띄우고

2. 서버에 Topic을 생성

3. Consumer로 생성한 Topic을 구독

4. Producer로 생성한 Topic에 메세지 전달

5. Consumer는 구독중이던 Topic에 메세지가 있는 걸 확인하고 읽어서 출력한다.



출처: https://debaeloper.tistory.com/24 



---

#### 카프카 실행하기

.\zookeeper-server-start.bat ..\..\config\zookeeper.properties

.\kafka-server-start.bat ..\..\config\server.properties

----



## 1. 윈도우에 카프카 설치

- 블로그 : https://oingdaddy.tistory.com/274



질문 -  wsl에 카프카 설치하고 연동 가능?



## 2. 설치한 카프카와 스프링부트 연동

블로그 참조 :

- 메인 : https://www.baeldung.com/spring-kafka

- 서브 : https://galid1.tistory.com/792

### 1. topic 생성

#### KafkaTopicConfig 클래스

- NewTopic 객체 이용

---

### 2. Producer

메세지를 생성하는 부분

#### [ KafkaProducerConfig 클래스 ]

- producerFactory()

  - kafka producer 인스턴스 생성

- **KafkaTemplate**
- producer 인스턴스 래핑 및, topic에 메세지 보내는 클래스

---

####  [ producer 클래스 ]

1. KafkaTemplate  주입받기

2. kafkaTemplate.send(topicName, message) 사용

- ListenableFuture 이용하면, 비동기 작업 가능


---

### 3. Consumer

메세지를 소비하는 부분

#### [ KafkaConsumerConfig 클래스 ]

- @EnableKafka
  - @KafkaListener 주석 감지용

---

#### [ consumer 클래스 ]

- @KafkaListener를 사용하여, 여러 리스너 구현하기

  - 하나의 주제에 대해 다른 그룹 id를 가진 여러 리스너 구현 가능.

  - group id가 consumer group??

  - ```java
    @KafkaListener(topics = "topicName", groupId = "foo")
    public void listenGroupFoo(String message) {
        System.out.println("Received Message in group foo: " + message);
    }
    ```

    

- 하나의 consumer, 여러개 topic 듣기 가능

  - ```java
    @KafkaListener(topics = "topic1, topic2", groupId = "foo")
    ```

- @Header 사용하기

  - 메세지 header를 검색할 수 있다.(질문... 메세지의 헤더가 뭐에요?)

  - ```java
    @KafkaListener(topics = "topicName")
    public void listenWithHeaders(
      @Payload String message, 
      @Header(KafkaHeaders.RECEIVED_PARTITION_ID) int partition) {
          System.out.println(
            "Received Message: " + message"
            + "from partition: " + partition);
    }
    ```

    

- 특정 파티션의 메세지 읽기

  - topic이 2개 이상의 partition으로 이루어진 경우, 특정 partition 명시적 구독 가능( + 초기 offset 지정 가능)

  - ```java
    @KafkaListener(
      topicPartitions = @TopicPartition(topic = "topicName",
      partitionOffsets = {
        @PartitionOffset(partition = "0", initialOffset = "0"), 
        @PartitionOffset(partition = "3", initialOffset = "0")}),
      containerFactory = "partitionsKafkaListenerContainerFactory")
    public void listenToPartition(
      @Payload String message, 
      @Header(KafkaHeaders.RECEIVED_PARTITION_ID) int partition) {
          System.out.println(
            "Received Message: " + message"
            + "from partition: " + partition);
    }
    ```

    
