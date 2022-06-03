####  파이썬 3.8로 설치하기

- 우분투에는 python 3.8로 뜨고
- jetconda에는 python 3.6 밖에 없다

 뭐임..?



usr/bin 의 파이썬 파일은 뭐고 - 3.8

which python 쳤을 때 나오는 경로의 파이썬 파일은 뭐임,..? - 3.6(python -V 치면 이걸로 나옴)



apt-get 으로 install 하는 것

pip install

의 차이는?



정답은,

"리눅스 환경변수설정"

- 모든 리눅스는, 쿠다든 파이썬이던지 명령어로 쓰는 프로그램들을, home의 .bashrc 파일에 불러오는 경로가 다 있어서
- 이거 경로만 잡아주고 source .bashrc로 적용만 시켜주면 된다!!!