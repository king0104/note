- select 
  - 컬럼을 선택하는 것이다
  - 
- from
  - 테이블을 선택하는 것이다
- group by
  - group the result set by one or more columns. 



### 한방 쿼리로 만들기!!!!





### post 관련

- spurs의 포스트들을 내림차순 정렬
- ![image-20210709184043359](C:\Users\4545a\AppData\Roaming\Typora\typora-user-images\image-20210709184043359.png)

- where 으로 조건 사용
- order by로 정렬



- 한방쿼리를 할라면, 중복되는 값들은 어떻게 하지? join하면서 지워야 하나?





### 컬럼의 default값 변경하기

![image-20210709183946168](C:\Users\4545a\AppData\Roaming\Typora\typora-user-images\image-20210709183946168.png)

위의 테이블의 아래의 컬럼을 timestamp 타입으로, 디폴트 값은 current_timestamp를 주겠다는 뜻이다.



### 디엠 창 만들기

1. 보내는 사람이 'subeen' 인 것만 추출
   1. 이 중에서 받는 사람의 이름 추출
   2. 받는 사람의 이미지 추출
   3. 언제 보냈는지 추출
   4. 읽었는지 안읽었는지 표시 
      1. 1일 지나면, 지난 날짜로 표시
      2. 1일 안지나면, 지난 시간으로 표시



### Follower수 user table의 nubOfFollowed에 넣어주기

![image-20210710000142475](C:\Users\4545a\AppData\Roaming\Typora\typora-user-images\image-20210710000142475.png)

1. 값을 변수로 받는다
2. update문을 사용해서 원하는 테이블(from)의 컬럼에 넣어준다.



### MYSQL 컬럼 삽입 및 삭제

![image-20210710024140847](C:\Users\4545a\AppData\Roaming\Typora\typora-user-images\image-20210710024140847.png)

#### 컬럼 추가

- alter table [테이블명] add [컬럼명] [타입] [옵션]; 

  ex) alter table [테이블명] add [컬럼명] varchar(100) not null default '0'; 

#### 컬럼 삭제

- alter table [테이블명] drop [컬럼명];



### distinct가 의미하는 바

MySQL에서 범주를 확인할 때 **SELECT DISTINCT**를 사용하는 것입니다.



하나, 예를 들어보겠습니다.

테이블에 카테고리라는 컬럼이 존재할 때,

이 카테고리 값이 테이블에 몇 종류가 있는지 알고 싶습니다.

그러면 카테고리를 조회할 때 이 값이 중복되면 안되기 때문에 DISTINCT를 사용합니다.



```mysql
SELECT DISTINCT 컬럼 FROM 테이블;
```



### 서브 쿼리 작성법

![image-20210710122920382](C:\Users\4545a\AppData\Roaming\Typora\typora-user-images\image-20210710122920382.png)

- 반복문의 중첩과 비슷하다고 생각하면 된다.
- 서브쿼리의 내용을 먼저 추출하고, 그 값을 메인쿼리에서 가져다 쓰는 방식이다
- 단일행 / 복수행 각각 사용하는 연산자 다르니 주의!! (예를 들자면, = 과 IN)

### 신기한 점 찾기

- select로 한번 컬럼 선택하면 그 아래 select문에서는 이미 선택한 컬럼들이 기본 값이 된다.





### 시행착오 및 오류

![image-20210709200243489](C:\Users\4545a\AppData\Roaming\Typora\typora-user-images\image-20210709200243489.png)

- select 하고 **from** 안해줘서 빨간줄 뜬거다....

