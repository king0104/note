### read()

```shell
ssize_t read(int fides, void *buf, size_t nbytes);
//윈도우에선 int형
```

- **read함수**는 파일에서 nbytes값의 크기만큼 바이트를 읽어서 buf에 저장합니다.



[리턴값]

- 성공시,
  - 읽어온 바이트의 수

- 실패시, 

  1. 파일의 끝에 도달했을 경우(EOF) – 0리턴
  2. **파일에 읽을 내용이 없을 경우 – 읽을 내용이 생길때까지 block!!!!!!!!!!!!!!**

  

- **다시 말해 사용 가능한 데이터가 없는 것과 파일 끝에 도착했다는 것에는 차이가 있다.**



### write()

```shell
ssize_t write(int fildes, const void* buf, size_t nbytes);
//윈도우에선 int형
```

- **write함수**는 buf에서 nbytes값의 크기만큼 바이트를 읽어서 파일 기술자(fd)에 작성합니다.
- 오류가 발생하면 -1을 반환하고 성공할 시 쓰기를 수행한 바이트 수를 리턴합니다.

