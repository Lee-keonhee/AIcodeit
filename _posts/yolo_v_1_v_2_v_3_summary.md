#### YOLOv2 작동방식
1. 입력 이미지를 CNN을 통해 Feature Map으로 변환
   - 예: 416x416 입력 이미지 → 13x13 Feature Map
<br>
2. 각 Grid Cell마다 Anchor Box를 사용하여 Bounding Box와 Classification Task 수행
   - 2-1. 각 Grid Cell은 K개의 Anchor Box를 계산한다 (보통 K=5)
     - 각 Anchor Box는 중심 좌표 x,y, width, height, Objectness Score를 가진다.
     - Objectness Score는 해당 박스에 객체가 존재할 확률과 예측 박스의 정확도를 반영
   - 2-2. 각 Anchor Box마다 Classification 수행
     - 클래스 수 C에 따라 SxSx(Kx5 + C) 형태의 Output을 생성
<br>
3. NMS(Non-Max Suppression)를 통해 겹치는 Box 제거
   - Confidence score 기준으로 낮은 박스 제거
   - 높은 Confidence 박스 순으로 정렬 후, IoU가 특정 threshold 이상인 박스 제거
   - 최종적으로 중복 없는 Bounding Box만 남김

#### YOLOv3 작동방식
1. 입력 이미지를 CNN (Darknet-53)으로 Feature Map 생성
   - Residual Block 사용으로 특징 추출 향상
<br>
2. Multi-scale Detection (FPN 구조) 적용
   - 13x13, 26x26, 52x52 Feature Map 사용
   - 작은 객체는 높은 해상도 Feature Map에서 탐지, 큰 객체는 낮은 해상도 Feature Map에서 탐지
   - Skip Connection으로 상위 Feature와 합성하여 작은 객체 성능 향상
<br>
3. 각 Grid Cell에서 Anchor Box를 사용하여 Bounding Box와 Classification 수행
   - 각 Grid Cell마다 K개의 Anchor Box 존재
   - Objectness Score와 클래스 확률 계산
   - Output 형태: SxSx(Kx5 + C)
<br>
4. NMS(Non-Max Suppression) 수행
   - 각 Scale에서 예측된 Bounding Box를 통합
   - Confidence Score와 IoU 기준으로 중복 박스 제거
   - 최종 Bounding Box 결정

