# Yolo(You Look OnLy Once)




[발표자료 다운로드(pdf)](https://github.com/dss-14th/deeplearning-repo-2/files/5764532/YOLO.You.only.look.once.pdf)



# FatRCNN
# YOLOv1
# YOLOv2
# YOLOv3
### [paper](https://pjreddie.com/media/files/papers/YOLOv3.pdf)

- yolov3 는 yolo9000과 같이 차원 클러스터링을 통해 앵커 박스로부터 바운딩 박스를 예측한다. 욜로 네트워크는 각 바운딩 박스로부터 4개의 좌표를 예측하고(tx, ty, tw, th), 각 그리드셀의 왼쪽 상단 지점을 기준으로 셀 내부의 위치를 예측해 최종 바운딩 박스 정보를 결정한다.(bx,by, bw, bh)

#### bounding box prediction
- yolov3 는 이진 분류를 통해 objectness score (바운딩 박스에 물체가 있는지 없는지에 대한 확률점수) 를 예측한다. ground truth box(정답으로 라벨링된 박스)와 IOU 가 가장 높은 바운딩 박스의 objectness score 는 1이 되어야 한다. 이 바운딩 박스를 제외한 objectness 가 threshold 값인 0.5를 넘는 값을 가진 바운딩 박스들은 모두 무시한다. 이전 yolo 버전과 다르게, 하나의 ground truth box 에 대해 하나의 바운딩 박스를 할당한다. ground truth box 에 할당되지 않은 바운딩 박스들은 좌표나 분류 예측예 대한 손실값을 반영하지 않는다. 

####  class prediction
- yolov2 의 경우, 클래스 분류시 소프트맥스를 사용해 하나의 대상에 대해 하나의 클래스만 대응되어, 멀티 라벨이 불가능하다는 문제가 있었다. yolov3 는 이를 해결하기 위해 시그모이드를 사용해 이진분류 문제로 바꾸면서 멀티라벨을 가능하게 했다. (ex) 여자, 사람)


#### predictions across scales
- yolov3 는 3개의 다른 scale 에서 앵커박스들을 생성하고, 바운딩 박스를 예측한다. 
