임베디드 환경에서 DarkNet이나 TensorFlow 같은 프레임워크로 학습한 모델을 실시간 구동하기 위해서 최적화 기법들이 필요하다. 본 논문에서는 DarkNet을 활용한 YOLOv4 모델을 학습한 결과에 TensorRT를 사용하여 GPU에 최적화 엔진을 만들고, 제공하는 정 밀도와 영상의 입력사이즈를 변경하여 최적의 모델을 찾는 것이 목적이다. 실험 결과 TensorRT Float32의 추론 속도가 DarkNet의 약 1.3배 빨라졌고, INT8 정밀 도에서는 1.6배 이상 빨라졌다. 입력 영상의 사이즈가 작을수록 더욱 좋은 성능을 냈으며 임베디드 보드에서 512x512 사이즈부터 Float16 정밀도가 30FPS 이상의 속도로 구동하여 실시간 검출에 사용할 수 있었다.



- https://www.eiric.or.kr/literature/ser_view.php?grp_gu=INME&f1=DS&gu=INME013E2&q1_yy=2020&q1_mm=08&cmd=qryview&SnxIndxNum=234610





- https://www.wenyanet.com/opensource/ko/604483a81dea4f612f490ee6.html



---

yolo를 onnx로 바꾸기

onnx -> trt 모델





