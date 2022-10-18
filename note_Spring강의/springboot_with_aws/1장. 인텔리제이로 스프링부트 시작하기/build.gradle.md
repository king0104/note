### build.gradle

#### buildscript

- gradle의 버전 관리를 한 곳에 집중할 수 있도록 해주는 것
- 이걸 사용해서 관리해야, 라이브러리들의 버전 관리가 한 곳에 집중되고, 버전 충돌 문제도 해결된다.



- ext

  - 전역변수 설정

  

#### 의존성

- 옵션

  - complie -> implemetation / api
  - implemetation : 메인 모듈이 사용하는 라이브러리 의존성
  - testImplemtation : test 모듈이 사용하는 라이브러리 의존성

  

- 의존성 작성법

  - '그룹:이름:버전'

  - 예시

    - ```java
      implementation('org.springframework.boot:spring-boot-starter-web') // 그룹:이름:버전
      ```

      



#### plugins / apply plugin

- 플러그인

  - 특정 작업을 하기 위해 모아둔 task의 모음
  - 맨 처음에 java가 들어가있는 것을 볼 수 있다.

  

- plugins(?)
  - 버전을 명시해주어야 한다.
  - buildscript와 함께 사용할 수 없음



-  apply plugin(?)
  - buildscript와 함께 사용할 수 있다
  - 버전을 명시하지 않으면, 전역변수의 버전을 따라간다