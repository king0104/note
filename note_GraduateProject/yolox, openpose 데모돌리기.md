#### 아나콘다 사용법
yolo 가상환경 : source activate yolo
openpose 가상환경 : source activate openpose
가상환경 나가기 : source deactivate
가상환경 내에서는 마음대로 뭐 설치하거나 해도 됌 
원하는 버전 설치 방법
예를들어 tensorflow 1.1.5를 설치하고 싶다?
conda install tensorflow==1.1.5
이고 버전을 바꾸고 싶다?
conda uninstall tensorflow 후
conda install tensorflow==2.1.0

pip install도 상관 없는데 pip install 에 없으면 conda에있는 경우가 많음



---



#### 현재 해야할 것

#### 1. 기본 개념

- 욜로 버전

  - 버전이 속도 빠른 순서대로
    Nano-Tiny-S-Darknet-M-L-X

  - 성능 좋은 순서대로 (test성능)
    X-L-Darnet-M-S-Tiny-Nano

- 욜로와 가상환경

  - 욜로 돌리기 전에 가상환경 들어가는거 잊지말기(가상환경에 욜로 돌리는 환경을 구현 함)
    가상환경 들어가는 명령어
    conda activate yolo
    나오는 명령어
    conda deactivate
  - 가상환경은, 파일 등 이런거 다 똑같은데 그냥 새로운 컴퓨터 하나를 준거라고 생각하면 되는건가?

  

#### 2. 욜로 돌리기

- 욜로 돌리기

  - 욜로 돌리는데 필요한건 다깔았음
    https://github.com/Megvii-BaseDetection/YOLOX
    욜로 깃허브이니까 여기서 예제 돌리는건 참고하고

    

- 해야할 것

  - 내가 이거 모델을 ~/YOLOX/models/ 에 넣어놨는데 이거 NX보드로 예제 돌려서 각 모델별로 얼마나 걸리는지 측정( 보고서 써야하니 캡쳐 ) 좀 해주라 (성능도 측정하면 좋음)



- ```
  python tools/demo.py image -n yolox-s -c /path/to/your/yolox_s.pth --path assets/dog.jpg --conf 0.25 --nms 0.45 --tsize 640 --save_result --device [cpu/gpu]
  ```

- 저기서 [cpu/gpu]는 gpu로 하고 path/to/your 뭐시기는 내가 넣어놓은 모델들로 설정 하고 저 save_result-device는 코드 뜯어봐야알듯





#### 욜로 돌리는 방법

1. 빌드에 필요한 요구사항 설치. 즉, requirement를 설치해주어야 한다

   - ```
     pip3 install -U pip && pip3 install -r requirements.txt
     ```

2. 빌드하기. python3 setup.py develop 실행

   - ```
     python3 setup.py develop
     ```



#### 에러

- conda로 설치한 것들 버전 확인하기

  - ```
    conda list
    ```

    



- 토치 버전

  - ```
    torch                     1.10.2                   pypi_0    pypi
    torchvision               0.11.3                   pypi_0    pypi
    
    ```

- 쿠다 버전

  - ```
    # nvidia-smi
    
    # nvcc --version
    
    # cat /usr/local/cuda/version.txt
    ```

  - 현재  10.2 이다.



- 변경사항
  - (yolo) python version 3.10.2 -> 3.9.0
  - torch==1.8.0 torchvision==0.9.1 torchaudio==0.10.0





#### 에러해결

-  meshgrid() got an unexpected keyword argument 'indexing'
  - ![image-20220309173257824](C:\Users\4545a\AppData\Roaming\Typora\typora-user-images\image-20220309173257824.png)
  - yv, xv = torch.meshgrid([torch.arange(hsize), torch.arange(wsize)])



- AssertionError: Torch not compiled with CUDA enabled

  - https://choice37.tistory.com/27 참고

  - torch와 cuda 버전이 안맞아서 생기는 문제

    - https://pytorch.org/get-started/previous-versions/ 에 들어가서 cuda 10.2에 맞는 torch 버전들 설치하려고 하는데, 되질 않는다...

      

  - https://forums.developer.nvidia.com/t/torch-not-compiled-with-cuda-enabled-over-jetson-xavier-nx/187310 참고해보기





