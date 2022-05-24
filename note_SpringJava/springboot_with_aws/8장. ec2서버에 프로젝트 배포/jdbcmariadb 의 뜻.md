## JDBC

- 자바에서 데이터베이스에 접속할 수 있도록 하는 자바 API
- 데이터베이스에서 자료를 쿼리하거나 업데이트하는 방법을 제공한다





#### 오류

- 데이터베이스 연결 설정을 위한 프로퍼티 파일에서, **jdbc:mariadb:// 에서 :** 를 빼먹었다...

```shell
# application-real-db.properties
spring.jpa.hibernate.ddl-auto=none
spring.datasource.url=jdbc:mariadb://springboot-with-aws.ccqzfdqmatff.ap-northeast-2.rds.amazonaws.com:3306/springboot_with_aws
spring.datasource.username= db name
spring.datasource.password= db pw
spring.datasource.driver-class-name=org.mariadb.jdbc.Driver

```

