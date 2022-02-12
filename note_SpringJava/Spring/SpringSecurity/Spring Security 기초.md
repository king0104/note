- 인증과 인가를 담담하는 프레임워크



#### 동작 구조

- 스프링시큐리티는 각각의 **역할에 맞는 작업을 처리하는 여러개의 필터들이 체인형태로 구성**되어 순서에 따라 순차적으로 수행됩니다.



### HttpSecurity 설정

> 스프링시큐리티의 각종 설정은 HttpSecurity로 대부분 하게 됩니다.
>
> - 리소스(URL) 접근 권한 설정
> - 인증 전체 흐름에 필요한 Login, Logout 페이지 인증완료 후 페이지 인증 실패 시 이동페이지 등등 설정
> - 인증 로직을 커스텀하기위한 커스텀 필터 설정
> - 기타 csrf, 강제 https 호출 등등 거의 모든 스프링시큐리티의 설정

`HttpSecurity는 스프링시큐리티의 거의 대부분설정을 담당`하는 객체 입니다.

---



- 인증
  - 로그인 느낌

- 인가
  - 로그인한 유저가 어떤 자원에 접근할 수 있는지 확인하는 것.
  - 

- 인증관리자 / 접근 결정 관리자 를 통해 리소스 접근 관리
- UsenamePasswordAuthenticationFilter /  FilterSecurityInterceptor

#### 인증



#### 인가

- `authorizeRequests()`

  - url에 따른 권한 승인

  - 로그인/회원가입 같은 부분은 모든 유저들에게 허용할 수 있도록 해야 한다. - permitAll() 사용

    - ```null
      .antMatchers("/api/auth").permitAll()
      .antMatchers("/api/user/join").permitAll()
      ```

  - 권한이 있는 유저만 허용

    - `.antMatchers("/api/**").hasRole(Role.USER.name())`
    - 

- `accessDecisionManager(accessDecisionManager())`

  - 

### 2-3. Authentication

- 모든 접근 주체(=유저) 는 Authentication 를 생성한다. 

- 이것은 SecurityContext 에 보관되고 사용된다. 즉 security의 세션들은 내부 메모리(SecurityContextHolder)에 쌓고 꺼내쓰는 것이다. 참고로 Authentication 인터페이스는 자주 쓰이니 알아둬야한다.



출처: https://sjh836.tistory.com/165 [빨간색코딩]