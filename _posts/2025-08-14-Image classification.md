---
layout: post
title:  "이미지 분류"
date:   2025-08-14 09:00:00 +0900
categories: [딥러닝, 인공지능, 데이터과학]
tags: [딥러닝 기초]
---
---
## 1. 이미지 분류
---

### 이미지 분류 정의

이미지 분류는 이미지 내의 특정 사물을 분류하는 것이다. 예를 들면, 아래 그림과 같이 강아지의 이미지를 보고 해당 사물을 강아지로 분류하는 것을 이미지 분류이라고 한다.

<img src="/assets/images/dog.jpg" width="300" height="200" alt="강아지">

[//]: # (![강아지 사진]&#40;/assets/images/dog.jpg&#41;)


### MLP(Multi Layer Perceptron)의 한계

- 이미지 평탄화(Flatten)작업이 필요 > 각 픽셀 간의 위치 정보를 잊게됨 > 인접 픽셀간 관계 학습이 어려움
- 평탄화된 모든 픽셀을 활용하여 pooutput 도출 > 파라미터 수 매우 증가 > 과적합 및 비용 증가


### CNN(Convolutional Neural Network)의 등장

이러한 다층 퍼셉트론의 한계를 보완하기 위해서 CNN이 등장하였다. CNN은 Convolution연산과 Polling을 통해, 이미지에서 특징(Feature)를 추출하는 네트워크이다.


