컨테이너 : 필요할 때 생성했다가, 필요없을 때 지우는 용도.

컨테이너를 삭제하면, 컨테이너 내부 파일 시스템에 작성한 내용이 전부 사라진다. 이것을 방지하기 위해, host의 파일 시스템과 연결해주자!

---

목표 : host의 파일시스템을 변경하면, container의 파일시스템에 반영되게 하기

- 그림으로 표현하면 다음과 같다
  - ![image-20220122201303164](C:\Users\4545a\AppData\Roaming\Typora\typora-user-images\image-20220122201303164.png)

- **실행환경은 container**
- **수정작업은 host**
  - 버전 관리도 용이
  - container는 생성 또는 삭제 마음대로 가능(실행자 역할 충실)
  - host, 즉 local의 파일을 변경하면 된다는 뜻이다!



- 코드

  - ```shell
    docker run -p 8888:80 -v C:\docker_htdocs\:/usr/local/apache2/htdocs/ httpd
    ```

  - -p : host포트 - container 포트 연결하는 옵션

  - -v : host의 파일시스템과 container 파일시스템 연결하는 옵션

    - 윈도우 기준 위와 같이 경로주기. 리눅스는 경로 지정 시 전부 다 /를 사용
    - 경로와 실행시킬 image 사이에 띄어쓰기 반드시 있어야!!(안그러면 argument error 뜬다)



