### jar 파일이란?

**JAR**(Java Archive) 파일이란  .jar 확장자 파일에 Class와 같은 Java 리소스와 속성 파일, 라이브러리 및 액세서리 파일이 포함되어 있어 JAVA 어플리케이션이 동작할 수 있도록 자바 프로젝트를 압축한 파일입니다.



----

#### 인텔리제이에서 jar 파일 만들기

- 우측의 gradle 탭 -> bootJar 누르기
- 그러면, 좌측 build 폴더/libs 폴더 내부에 jar 파일 생성되어있다.



----

#### 로컬에서 jar 파일 실행하기(윈도우)

1. jar 파일이 있는 위치에서 cmd창 열기
2. java -jar [jar파일명].jar 명령어 입력





- JDK 버전이 중요하다.
- jar 파일을 만들 때 jdk 버전과, jar 파일을 실행할 때 jdk 버전이 같아야 한다