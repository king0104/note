#### yolox?



#### yolo를 트레인한다는 뜻은?

- yolo 코드를 받는다
-  data/img 폴더에, jpg 파일을 넣는다 (학습시킬 데이터)
  - jpg 파일은 어떤 객체인지 라벨링이 된 이미지이다.
- train.txt 파일을 만든다
- ./ 어쩌구저쩌구 이용해서 학습을 진행한다



<학습 후, 새로운 파일 생성됨 : yolox_outputs>

- 학습이 끝나면, weight 파일이 생성된다
- weight 파일로, 어떤 이미지를 인식해보는 것이다.



#### yolo 모델이라는 뜻은?

- 학습 후 생성된 파일을 말한다. 즉, weight 파일이다
- yolox 에선, pytorch weight 라고 해서, **.pth** 파일이다.



#### 우리가 데이터셋으로 트레인 진행한 것은?





#### yolo를 실제로 사용하는 방법은?

