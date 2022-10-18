## 보안그룹

![image-20220503183435043](C:\Users\4545a\AppData\Roaming\Typora\typora-user-images\image-20220503183435043.png)

- 보안 그룹이 2개이다
- 각 인스턴스마다 보안 그룹을 만든다고 생각하면 된다!!



- 신기하게, 보안그룹2에 보안그룹 1의 ssh를 적용하면 ssh 접속이 안된다. 왜지..?

---

#### 보안그룹 1

- ssh 연결을 위한 보안그룹
- ec2에 터미널로 접속할 때



- 인바운드 규칙

  - TCP, 8080, 0.0.0.0/

  - HTTPS, 443, 0.0.0.0/

  - **SSH, 22, 현재 내 IP**

    - 집 이외에 다른 곳에서 EC2 접속하면, 그곳의 IP를 추가하도록 하자. 보안상의 이유 때문이다.

    

- ![image-20220503184211915](C:\Users\4545a\AppData\Roaming\Typora\typora-user-images\image-20220503184211915.png)





#### 보안그룹 2

- EC2 / 로컬 컴퓨터에서 rds 접속할 때

- 인바운드 규칙에

  1. **EC2의 보안 그룹 id** 
  2. **현재 접속하려는 컴퓨터의 ip**

  를 추가해주어야 한다.

  

- 인바운드 규칙

  - 유형 : mysql/aurora

  - 프로토콜 : TCP

  - 포트 : **3306** (mysql은 기본적으로 3306포트로 외부 접근을 받게 되기 때문!!!!)



- ![image-20220503184037131](C:\Users\4545a\AppData\Roaming\Typora\typora-user-images\image-20220503184037131.png)