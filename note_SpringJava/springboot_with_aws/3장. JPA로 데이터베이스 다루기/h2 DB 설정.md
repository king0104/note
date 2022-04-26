## H2 database

- 손쉽게 사용 가능
- build.gradle에 의존성만 추가해주면, 바로 사용 가능하다



#### h2 옵션 설정 - application.properties

<기본 설정>

H2에 대한 설정이 따로 없으면, 기본 설정은 아래 코드와 같다.

```properties
spring.datasource.url=jdbc:h2:mem:testdb  
spring.datasource.driverClassName=org.h2.Driver  
spring.datasource.username=sa  
spring.datasource.password=  
spring.h2.console.enabled=false  
```



<추가설정>

- SQL문 콘솔에서 확인하기

    - ```properties
      spring.jpa.show_sql=true
      ```

    

- H2용 쿼리 -> MYSQL 쿼리로 바꾸기 (1)

    - ```properties
      spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.MySQL5InnoDBDialect
      
      spring.datasource.url=jdbc:h2:mem:testdb;MODE=MySQL;DATABASE_TO_LOWER=TRU
      ```

    

- 웹 콘솔(=웹브라우저) 통해서 db에 직접 접근하기

  - ```properties
    spring.h2.console.enabled=true
    ```

  - 위 설정 후, 스프링 실행 -> http://localhost:8080/h2-console 접속하기 -> JDBC URL = jdbc:h2:mem:testdb 로 설정 후 -> connect 버튼

