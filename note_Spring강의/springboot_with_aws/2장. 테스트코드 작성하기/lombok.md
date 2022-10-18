### Variable not initialized in the default constructor

- 롬북을 통해 생성자를 만들고 해당 오류가 뜨면, 
  - **자신의 gradle 버전에 맞는 방법으로 롬북 의존성**을 추가해주어야 한다



- gradle 5.x 미만

  - ```java
    dependencies {
      implementation 'org.projectlombok:lombok'
    }
    ```

- gradle 5.x  이상

  - ```java
    dependencies {
      compileOnly 'org.projectlombok:lombok'
      annotationProcessor 'org.projectlombok:lombok'
    }
    ```