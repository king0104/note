

#### 카프카 사용 시, 생각해야 할 것

- **producer는 누구이고, 무엇을 produce 해야하는지?**
- **consumer는 누구이고, 무엇을 consume 해야하는지?**
- 직렬화 / 역직렬화

---

#### '카프카를 사용한다는 것'의 의미

- 어떤 메세지(객체나 string이나 다 된다)가 끝(컨트롤러)에서 끝(db)으로 전달되는 상황을 생각하자.
- **여기서 카프카를 사용한다는 뜻은, "카프카라는 중간통로를 (반드시) 거치는 것이다!!"**
- 중간 통로는, producer -> consumer 구조로 되어있다.

- 중간 통로가 존재함으로써, 여러 개의 작업을 비동기적으로 처리할 수 있다. (메세지를 보내는 작업, 메세지를 소비하는 작업을 분리하니까, 효율적임)



---

#### producer : 메세지 생성 & 전달

- **메세지를 만들어, 전달하는 주체.**
- 여기서는, user라는 메세지를 만들어야 한다.
  - 실제로 user를 만들어서 넣어준다고 생각하면, service 계층을 사용하게 되는건가요??(질문)
  - 1. service에서 user 생성
    2. service에서 sendMessage 호출
  - (질문) spring 코드를 짜는 정형화된 패턴 같은 느낌을 알고 싶은데 참고할 만한게 있을까요? controller나 service 이런건 어떤 방식으로 작성하는게 정석인가 궁금해서요

---

- 메세지 생성 및 전달하기

  - kafkaTemplate이라는 객체(편지'봉투'라고 생각하면 된다)에 메세지를 담아 전달한다.

  - **편지의 내용에 따라 편지봉투가 달라져야 한다.** 즉, 메세지의 내용에 따라 메세지 봉투가 달라져야 한다.

    - 그래서, 편지 봉투에 대한 설정 중 **어떤 메세지를 담을 것인지를 정해주어야 한다.**

    - 그러므로, 설정 클래스에서 **VALUE_SERIALIZER_CLASS_CONFIG 에 메세지를 직렬화한 클래스**를 넣어주어야 한다.

      - String : StringSerializer
      
      - **직접 만든 객체 : JsonSerializer**
      
      - ```java
        // KakfaProducerConfig class(즉, 설정 클래스)
        
        @Bean
        	// 1. <String, User> 사용
            public ProducerFactory<String, User> producerFactory() {
                Map<String, Object> configProps = new HashMap<>();
                configProps.put(
                        ProducerConfig.BOOTSTRAP_SERVERS_CONFIG,
                        bootstrapAddress);
                // 2. StringSerializer.class 사용
                configProps.put(
                        ProducerConfig.KEY_SERIALIZER_CLASS_CONFIG,
                        StringSerializer.class);
                // 3. JsonSerializer.class 사용
                configProps.put(
                        ProducerConfig.VALUE_SERIALIZER_CLASS_CONFIG,
                        JsonSerializer.class);
                return new DefaultKafkaProducerFactory<>(configProps);
            }
        
        	// <String, User> 사용
            @Bean
            public KafkaTemplate<String, User> kafkaTemplate() {
                return new KafkaTemplate<>(producerFactory());
            }
        ```
      
        
      





#### consumer : 메세지 받기 & 해당 메세지로 어떤 동작 수행

- **메세지를 받아, 메세지를 통해 어떤 동작을 수행하는 주체**
- 여기서는, user라는 메세지를 받아 DB에 저장해야 한다.



- 메세지 받기 및 동작 수행

  - KafkaConsumerConfig 또한, deserializer 타입 맞춰서 설정해주기.

  - 추가적으로, JsonDeserializer는 반드시 재구현 후 사용해야한다!!!!!!

    - 그 이유는 Producer의 GCMPushEntity의 패키지명과 Consumer의 User 패키지명이 달랐기 때문이다. 만약 package명이 다르다면 다른 객체로 판단하기때문에 **deserializer.addTrustedPackages(“\*”);** 메서드로 해당 패키지를 신뢰할 수 있도록 추가해줘야한다. 

    ---

    - 방법( config 클래스에 작성 ) 

    1.  JsonDeserializer 재구현

    ```java
    private JsonDeserializer<User> userJsonDeserializer() {
    	JsonDeserializer<User> deserializer = new JsonDeserializer<>(User.class);
    	deserializer.setRemoveTypeHeaders(false);
    	deserializer.addTrustedPackages("*");
    	deserializer.setUseTypeMapperForKey(true);
    	return deserializer;
    }
    ```

    2. 만든 deserializer 실제 사용

    ```java
    @Bean
        public ConsumerFactory<String, User> consumerFactory() {
    
            JsonDeserializer<User> deserializer = userJsonDeserializer();
    
            Map<String, Object> props = new HashMap<>();
            props.put(
                    ConsumerConfig.BOOTSTRAP_SERVERS_CONFIG,
                    bootstrapAddress);
            props.put(
                    ConsumerConfig.GROUP_ID_CONFIG,
                    groupId);
            props.put(
                    ConsumerConfig.KEY_DESERIALIZER_CLASS_CONFIG,
                    StringDeserializer.class);
            props.put(
                    ConsumerConfig.VALUE_DESERIALIZER_CLASS_CONFIG,
                    deserializer);
    		// 여기에, 파라미터 3개 반드시 전부 다 넣어줘야 한다!!!(안넣어서 삽질..)
            return new DefaultKafkaConsumerFactory<>(
                    props, new StringDeserializer(), deserializer);
        }
    ```

    



