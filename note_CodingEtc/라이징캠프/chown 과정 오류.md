## chown 과정 오류

1. operation not permitted / permission denied 뜸. chown 과정 중에서

![image-20210623012531133](C:\Users\4545a\AppData\Roaming\Typora\typora-user-images\image-20210623012531133.png).

<해결>

- root 계정으로 로그인 해야 한다 -> sudo su 입력 후 비밀번호 입력
- sudo 넣어서 잠시만 root 계정으로 로그인 한 효과 사용





2. 하지만 초기화 과정에서 오류 남

### 데이터베이스 초기화

```
/usr/local/# cd mysql
/usr/local/mysql# mkdir mysql-files

/usr/local/mysql# chown -R mysql:mysql /usr/local/mysql 
=> /usr/local/mysql의 모든 파일을 "소유자 : 소유그룹" 으로 바꾸기
=> -R 붙임. 재귀적으로 적용한다는 뜻. 파일과 디렉토리에 재귀 적용. 
=> 즉 ,경로의 모든 것에 적용한다는 뜻

/usr/local/mysql# chown mysql:mysql mysql-files

/usr/local/mysql# chmod 750 mysql-files
=> r : 읽기권한(4) , w : 쓰기권한(2), x : 실행권한(1)
=> 소유자권한 : 읽기, 쓰기, 실행
=> 그룹권한 : 읽기, 실행
=> 전체권한 : 없음

```

- ![image-20210623014400804](C:\Users\4545a\AppData\Roaming\Typora\typora-user-images\image-20210623014400804.png)

  - aborting이라고 뜬다

  - 뭐 이미 있다는 느낌

  - 삭제하면 된다는 느낌

    mysql-files 삭제하고 다시 진행해도 안된다. 똑같은 오류 계속 난다

    

- 한번 서버 자체를 종료해보려고 함.

![image-20210624063655868](C:\Users\4545a\AppData\Roaming\Typora\typora-user-images\image-20210624063655868.png)

서버 종료시 (2) 에러 뜸. 이거 어떻게 해결하냐?

계속 sock어쩌구 에러 뜨는듯





3. 아니 에러 로그 파일 찾고 싶은데 왜 난

var/log/ 뒤에 경로가 없냐? 이거 어떻게 찾는지 알아보기

(아래 경로가 예시)

![image-20210624053254659](C:\Users\4545a\AppData\Roaming\Typora\typora-user-images\image-20210624053254659.png)





4. 서버 실행시

```null
/usr/local/mysql/bin# ./mysqld_safe --user=mysql &
```

![image-20210624054439368](C:\Users\4545a\AppData\Roaming\Typora\typora-user-images\image-20210624054439368.png)

- yoon virtual box.err 에서 에러 확인하기
  - 권한 없다고 뜸 -> chmod로 실행 권한 주기

![image-20210624054704994](C:\Users\4545a\AppData\Roaming\Typora\typora-user-images\image-20210624054704994.png)

​			아 이거 권한 잘못 줬다가 text file busy 뜸.

​			어차피 나 root이니까 root에 대한 권한 설정만 read가 있으면 되는건데 삽질함

​			yoon-어쩌구 파일 열기만 하면 되니까 명령어 **cat** 사용

![image-20210624060121112](C:\Users\4545a\AppData\Roaming\Typora\typora-user-images\image-20210624060121112.png)



- starting mysqld daemon ... 오류

  ![image-20210624145612439](C:\Users\4545a\AppData\Roaming\Typora\typora-user-images\image-20210624145612439.png)

  해결했는데, 원래 존재한다고 뜸

  - This is because the mysql process has already been started, so it needs to be killed and then started. The code is as follows

    ps -aux |grep mysql  #View mysql process id
    kill -9 7328
    ps -aux |grep mysql  #Check again to make sure there is no mysql process
    ./bin/mysqld_safe --user=root &  #start up

  => 응 이래도 안돼,,, 원래 계속 존재한ㄷ=대..



#### 느낌상 서버가 현재 없는 상태이거나 있는 상태이거나 데이터베이스가 있는 상태이거나 없는 상태여서 이런건데 이걸 어떻게 해결하지...? 일단 문제는, "데이터베이스 초기화 과정" 에서 일어났다는 것이다. 그쪽 관련 에러를 해결해보자.



아... 진짜 미쳤다

데이터베이스 초기화

서버 실행  

서버 연결

서버 종료

순으로 진행하는 것인데



내가 계속 서버 연결 안하고 계속 서버 종료 해보고 서버 실행 해봐서 그런거다. 심지어 서버 실행 시에 블로그랑 나랑 똑같이 나오는데 왜 난 그게 오류라고만 생각했지? 다시 보니까 똑같은 메세지 떠있고 그 다음 서버 연결 하는 건데... 후...

어쨌든 서버 연결 하니까 잘 됐다. 다행이다.



<이 삽질로 배운 점>

sudo의 의미



디렉토리와 파일 색



ls -a : 디렉토리,파일 종류 보기

ls -l : 디렉토리, 파일 상세한 내용까지 보기

​	=> 이때 소유자, 그룹, 외부인 세개가 따로 각각의 권한을 가지고 있다는 것을 알 수 있음

​	=> 디렉토리, 파일 구별법 : 앞부분에 -가 붙으면 파일

​	=> 앞부분 세파트씩 나눠서 소유자,그룹, 외부인 권한 표시. 각각의 rwx 으로 읽기, 쓰기, 실행 권한 있다는 것을 	의미



chown, chmod 명령어

파일을 실행할 때 명령어 : ./



vim 편집법

	1. :q 종료 :!q 강제종료 :wq 저장 후 종료
 	2. 삽입모드 - insert , 명령모드- ' : '





