## spring -> spring boot

setter 주입 알아보기.

예를 들어, Controller에 필드로 존재하는 MemberDao를 setter 메서드로 가져오는 것임.



---

### 내가 진행하는 것

- [x] (maven 프로젝트명을 ABC 라고 한다면 구조는 **parent인 ABC와 child로 ABC-web, ABC-common** 이 있다. )

  이게 뭔뜻일까...? 구조가 parent - child가 있다고?

  출처: https://oingdaddy.tistory.com/18 [SI Supply Depot] 

  => parent/child 구조로 만들어서 그런 것이다. 난 지금 project 한개에 대해서만 pom.xml 설정하고 있기 때문에, 하나의 pom.xml에다가 모든 설정 해주면  된다.





- [x] 에러 해결중 - 버전이 안맞다고 뭐라고 함 

- https://stackoverflow.com/questions/27037657/stop-intellij-idea-to-switch-java-language-level-every-time-the-pom-is-reloaded/27037879



- [ ] 스프링 설정 클래스 없애기
  - [ ] 설정 클래스 삭제
  - [x] 기존의 주입 관계 확인 -> 1. 생성자 주입 / 2. setter 주입
  - [x] controller,service,dao 들어가서 새로운 주입 관계로 바꾸기 -> lombok 사용



- [ ] 스프링부트 datasoure관련 에러



#### 에러

- [ ] ![image-20210918190533088](C:\Users\4545a\AppData\Roaming\Typora\typora-user-images\image-20210918190533088.png)

  java: lambda expressions are not supported in -source 1.6
    (use -source 8 or higher to enable lambda expressions)

  



- [x] For artifact {org.springframework.boot:spring-boot-starter-web:null:jar}: The version cannot be empty.

  =>![image-20210919024124259](C:\Users\4545a\AppData\Roaming\Typora\typora-user-images\image-20210919024124259.png)

  artifactId를 spring-boot 에서 spring-boot-starter-parent로 수정!!

  

- [ ] ![image-20210918190409032](C:\Users\4545a\AppData\Roaming\Typora\typora-user-images\image-20210918190409032.png)![image-20210918190350697](C:\Users\4545a\AppData\Roaming\Typora\typora-user-images\image-20210918190350697.png)

  위의 코드를 추가하면, 아래의 오류가 뜬다.



---

#### springboot 메인 클래스 만들기

application.java

@SpringBootApplication = @SpringBootConfiguration + @ComponentScan + @EnableAutoConfiguration 

@ComponentScan 도 자동으로 들어가있는데 자동설정으로 사용하게 된다면 스캔하는 위치는 Application.java 가 위치한 패키지 기준으로 스캔한다고 보면 된다.



#### 정적 자원 위치 변경

springboot에서는 정적자원을 읽어오는 위치는 classpath:/static, classpath:/public, classpath:/resources 이다. 





---

1. web.xml 에 의존성 추가하기

   왜 2.5.4 RELEASE는 추가가 안되고 2.1.4는 되는거지?

- 의존성(dependency)
  - 원하는 라이브러리를 적으면, maven repository에서 가져온다. 심지어 해당 라이브러리가 참조하는 또 다른 라이브러리들을 모두 찾아서 추가해준다. 이것을 의존성 전이라고 한다.



- plugin 태그는 뭘 의미하는거지...?
  - maven repository에서 가져오는 모든 것
  - 메이븐을 동작시키기 위해 사용하는 외부 소스 파일이라고 생각하자

- jar/war 이게 어떤 역할이지...?
  - 플러그인의 한 종류.
  - 그 중 압축 도구의 역할을 한다.

---

## 6. POM.xml

pom.xml 은 메이븐을 이용하는 프로젝트의 root에 존재하는 xml 파일이다. pom은 프로젝트 객체 모델(Project Object Model)을 뜻한다. 프로젝트 당 1개가 있다. 이것만 보면 프로젝트의 모든 설정, 의존성 등을 알 수 있다!!

### 엘리먼트

- `<groupId>` : 프로젝트의 패키지 명칭

- `<artifactId>` : artifact 이름, groupId 내에서 유일해야 한다.

  ```
    <groupId>org.springframework</groupId>
    <artifactId>spring-webmvc</artifactId>
  ```

- `<version>` : artifact 의 현재버전 ex. 1.0-SNAPSHOT

- `<name>` : 어플리케이션 명칭

- `<packaging>` : 패키징 유형(jar, war 등)

- `<distributionManagement>` : artifact가 배포될 저장소 정보와 설정

- `<parent>` : 프로젝트의 계층 정보

- `<dependencyManagement>` : 의존성 처리에 대한 기본 설정 영역

- `<dependencies>` : 의존성 정의 영역

- `<repositories>` : 이거 안쓰면 공식 maven 저장소를 활용하지만, 사용하면 거기 저장소를 사용

- `<build>` : 빌드에 사용할 플러그인 목록을 나열

- `<reporting>` : 리포팅에 사용할 플러그인 목록을 나열

- `<properties>` : 보기좋게 관리가능, 보통 버전에 많이 쓴다.

  ```
    <!-- properties 에 이렇게 추가하면 -->
    <spring-version>4.3.3.RELEASE</spring-version>
  
    <!-- dependencies 에 이렇게 쓸수 있다. -->
    <version>${spring-version}</version>
  ```

### 큰 뼈대

```
<modelVersion>4.0.0</modelVersion>

<!-- The Basics -->
<groupId>...</groupId>
<artifactId>...</artifactId>
<version>...</version>
<packaging>...</packaging>

<dependencies>...</dependencies>
<parent>...</parent>
<dependencyManagement>...</dependencyManagement>
<modules>...</modules>

<properties>...</properties>

<!-- Build Settings -->
<build>...</build>
<reporting>...</reporting>

<!-- More Project Information -->
<name>...</name>
<description>...</description>
<url>...</url>
<inceptionYear>...</inceptionYear>
<licenses>...</licenses>
<organization>...</organization>
<developers>...</developers>
<contributors>...</contributors>

<!-- Environment Settings -->
<issueManagement>...</issueManagement>
<ciManagement>...</ciManagement>
<mailingLists>...</mailingLists>
<scm>...</scm>
<prerequisites>...</prerequisites>
<repositories>...</repositories>
<pluginRepositories>...</pluginRepositories>
<distributionManagement>...</distributionManagement>
<profiles>...</profiles>
```



출처: https://sjh836.tistory.com/131 [빨간색코딩]

