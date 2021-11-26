#### SSH 프로토콜  - 포트번호 : 22





#### 인바운드 / 아웃바운드

- 인바운드

  

#### mysql 접속 / 나가기

- sudo mysql
- exit



#### nginix

- php와 다르게, fpm 설치가 추가된다 - 이유가 뭔지 알아보기
- nginix 기본 경로 :  cd /var/ww/html/
  - 여기에 들어있는 .html 파일 하나 => nginix 창을 띄워주는 파일
  - sudo vi index.php -> phpinfo()  만들기
  - sudo vi /etc/nginx/sites-available/default -> 들어가서 php 부분 주석 해제 -> 연동
  - sudo service nginx restart
- 과정 끝난 후, ip주소/index.php 들어가면 phpinfo() 화면이 잘 나오는 것을 볼 수 있음



### DATAGRIP 사용하기

1. database -> mysql 클릭

2. localhost의 name : aws에서 만든 서버 외부 주소 입력 - ex) 52.79.73.125

3. password

   - password 찾기

     1. putty 창 열기

     2. sudo mysql

     3. use mysql

        * **use database_name 명령어**
          - 데이터베이스를 선택할때 사용하는 명령어
          - sql명령어 실행 시에, 어떤 데이터베이스에 적용해야 하는지 모르기 때문에, 문서의 제목을 찾는 것과 동일한 기능이라고 생각하면 된다.(즉, 특정 데이터베이스를 선택하는 것)
          - database changed라는 메세지가 뜨면 그 데이터베이스가 선택된 것이다.

     4. show databases

     5. show tables

     6. select user, host from user

        - 여기서 user 선택하고 그 user로 password 설정한다!!

        - 이전에는 다 root 계정으로 password 만들었지만, 보안상 다른 user로 하는 것이 좋다

          (mysql -u root -p 명령어 이용)
          #### 1. 새로운 user 만들기

          0. $ sudo mysql -u root -p : root계정으로 mysql 접속

          1. mysql> create user 'lumin'@'%' identified by 'password';  

             : 외부에서 접속 가능한 유저 만들기

             **'Username'@'%'** : 해당 사용자는 외부에서 접근가능

             **'Username'@'localhost'** : 해당 사용자는 내부에서만 접근 가능

             **'Username'@'xxx.xxx.xxx.xxx'** : 해당 사용자는 지정한 ip주소로만 접근 가능

          #### 2. 데이터 베이스 생성

          #### 3. 데이터베이스 권한 부여

          #### 4. mysql 외부접속 설정

          MySQL의 설정 파일인 **/etc/mysql/mysql.conf.d/mysqld.cnf** 를 수정합니다.

          $ cd /etc/mysql/mysql.conf.d 

          $ sudo vim mysqld.cnf

          #### 5. 포트포워딩

          AWS 인스턴스 서버 들어가서 인바운드 규칙 수정 - mysql 규칙 추가하기

          #### 6. DATAGRIP으로 외부에서 MYSQL 접속

          

