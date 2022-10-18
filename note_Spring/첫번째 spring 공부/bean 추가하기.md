1. XML 파일 만들기
   - 고전적인 방법
2. Java 설정 파일 사용하기( 설정 클래스 만들기)
   - ApplicationConfig.java 만들고, @Configuration 붙이기
   - 빈으로 등록할 객체를 리턴하는 메서드를 정의하고, @Bean 을 붙인다.
   - bean id : 메서드명
   - return 타입 : bean 타입
   - return하는 객체 : bean 객체
   - 의존성 - setter 주입