## EC2 key 분실... 조치 방법 

### 기본 용어

#### 볼륨

- 인스턴스에 연결되는 하드웨어 장치라고 생각하면 된다.
- 인스턴스의 정보를 담고 있는 하드웨어



#### mount 명령어

- 리눅스는 하드 드라이브, 시디롬, USB 등등 기타 외의 물리적인 장치 파일 시스템으로 인식되어야 사용 할 수 있습니다. 이러한 하드웨어 장치를 액세스 하기 위해서는 특정한 위치에 연결해 주어야 하는데 이러한 과정을 마운트라고 합니다.
- 즉, **볼륨이라는 하드웨어 장치를 인스턴스에 연결하기 위해 사용하는 것**이다.



- 임시 ec2에 attach한 볼륨을 마운트(실제로 사용할 수 있도록 하기) 할 때사용한다

```shell
 sudo mount /dev/sdf1 /mnt
```



#### cat 명령어 + >, >>

- **> 기호**를 사용하면 기존에 있는 파일 내용을 지우고 저장하고

- **>> 기호**를 사용하면 기존 파일 내용 **뒤에 연속해서 기록**합니다. 



- 분실된 ec2 공개키를, 임시로 만든 ec2의 공개키로 바꿀 때 사용한다.

```shell
cat /home/ec2-user/.ssh/authorized_keys > /mnt/home/ec2-user/.ssh/authorized_keys
```

---

### 대략적 과정

1. 임시 ec2 생성

2. 임시 ec2의 키 페어 저장해두기

3. 분실된 ec2의 키 페어를 임시 ec2의 키 페어로 교체하기

   1. 분실된 ec2 볼륨 detach

   2. 임시 ec2에 분실된 ec2의 볼륨 attach

   3. 임시 ec2에서 분실될 ec2의 볼륨 monut

   4. cat 명령어로 분실된 ec2의 키페어 교체



4. 분실된 ec2의 볼륨, 임시 ec2에서  detach
5. 분실된 ec2 볼륨, 분실될 ec2에 attach
6. 인스턴스 시작



----

### 참고

아래의 두 블로그를 참고하자

https://blog.nuricloud.com/ec2-key-pair-%EB%B6%84%EC%8B%A4/

http://pyrasis.com/book/TheArtOfAmazonWebServices/Chapter07/01