### bazel이란?

소프트웨어 빌드 및 테스트 자동화를 가능하게하는 오픈 소스 도구입니다. 머신러닝 프레임워크인 텐서플로우(Tensorflow)뿐만 아니라 구글 내부 프로젝트 및 많은 오픈소스 등에도 사용됩니다.



https://hiseon.me/c/bazel-tutorial/



#### 바이너리 릴리즈..?

- bin 파일을 깃허브에 올려놓은 걸 뜻하는 듯 하다.
- 다운받고, 옮겨넣기



#### binary vs repository

- binary는 직접 홈피에서 설치파일 받아서 ./로 설치 하는것

- repository가 뭐냐면 sudo apt install 혹은 sudo apt-get install로 ubuntu library에서 가져와서 설치 하는것



#### 리눅스에서 다운받기

- Bazel을 설치하려면 먼저 Bazel 저장소를 apt로 설치할 수 있도록 저장소와 그에 맞는 키를 등록해줘야 합니다. 두 가지 모두 리눅스 사용자들에겐 흔히 접하는 상황이나 그렇지 않은 분들은 좀 당황스럽고 난해하게 느껴질수도 있을 것 같습니다. 
  쉽게 말하면 Bazel을 내려받을 주소를 리눅스에 알려주고 -> 올바른 설치인지 인증하기 위해 키를 등록해주고 -> 설치 이렇게 보시면 됩니다.