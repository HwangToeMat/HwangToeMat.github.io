---
title: 3. Faster R-CNN 논문 리뷰
image: https://github.com/HwangToeMat/HwangToeMat.github.io/blob/master/Paper-Review/image/FasterRCNN/img0.jpg?raw=true
description: >
 Faster R-CNN - Faster R-CNN을 읽고 논문 주요내용을 정리해본다.
author: author1
layout: post
order: 10
---
# [Object Detection]  3. Faster R-CNN 논문 리뷰

<a href="https://arxiv.org/abs/1506.01497">[PDF] 논문원본</a>

# Faster R-CNN: Towards Real-Time Object Detection with Region Proposal Networks

## 모델 구조

<img src="https://github.com/HwangToeMat/HwangToeMat.github.io/blob/master/Paper-Review/image/FasterRCNN/img1.png?raw=true" style="max-width:100%;margin-left: auto; margin-right: auto; display: block;">

**Faster R-CNN**에서는 이전의 Fast R-CNN과 R-CNN 모델에서 가장 많은 시간을 소요했던 **Selective Search 단계를 제거**하고 **RPN(Region Proposal Network)를 통해 ROI**를 구한다. RPN은 GPU에서 효율적인 계산이 가능한 구조이기 때문에 **속도가 향상** 되었고 ROI를 구하는 과정(RPN) 자체를 학습하여 **정확도를 높였다.**

### 1단계. CNN

이전의 Fast R-CNN과 R-CNN과는 다르게 Selective Search를 진행하지 않고 input 이미지 한장을 그대로 집어 넣는다.

### 2단계. Region Proposal Network(RPN)

<img src="https://github.com/HwangToeMat/HwangToeMat.github.io/blob/master/Paper-Review/image/FasterRCNN/img2.png?raw=true" style="max-width:100%;margin-left: auto; margin-right: auto; display: block;">

RPN은 앞서 CNN의 output으로 나온 feature map을 input값으로 갖는다. 그리고 그림과 같이 **anchor의 사이즈를 크기별, 종횡비(2:1, 1:1, 1:2...)별로 미리 지정**해 둔다. 

RPN이 진행되면서 filter가 feature map을 슬라이딩 할때 해당 위치의 n anchor에 대한 **n score(해당위치에 물체가 있는지 여부)와 4n coordinates(생성된 ROI의 좌표)가** 생성된다.

이때 n anchor의 **IoU(Intersection over Union)값**을 기준으로 각각 **positive label**과 **negative label**을 달아 학습을 진행한다.

마지막으로 **n score의 값이 높은 순서대로 anchor를 나열**하여 Bounding Box Regression을 진행하고 **ROI값을 구한다.**

* RPN loss function

<img src="https://github.com/HwangToeMat/HwangToeMat.github.io/blob/master/Paper-Review/image/FasterRCNN/img3.png?raw=true" style="max-width:100%;margin-left: auto; margin-right: auto; display: block;">

> N<sub>cls</sub> = mini-batch 의 크기
>
> N<sub>loc</sub> = anchor location의 개수
>
> L<sub>cls</sub> = classificaion loss(물체가 있는지)
>
> L<sub>loc</sub> = bounding box regression loss 

### 3단계. Classification & Bounding Box Regression

마지막으로 지금까지 나온 값들을 사용하여 Classification과 Bounding Box Regression을 진행하여 loss 값을 얻는.

**Classification에서는 softmax**를 사용하여 분류하였고, **bounding box regression에서는 Linear**를 통해 regression하였다.

## 학습과정

R-CNN에서는 Classification과 Bounding Box Regression을 따로 학습하였고. Fast-RCNN에서는 두 가지를 합쳐 Multi-task Loss로 학습을 진행하였다.

하지만 Faster R-CNN에서는 **ROI를 구하는 과정(RPN)도 같이 학습시키기 때문에 총 4개의 loss로 학습을 진행한다.**

> 01. Imagenet에 pretrained된 모델로 **RPN의 학습**을 진행한다. 
>
> 02. 학습된 RPN에서 Region Proposal에 쓰인 layer만 가져와 **Fast R-CNN을 학습**시킨다.
>
> 03. 학습된 RPN과 Fast R-CNN을 가져와 다른 weight는 고정하고 **RPN에 해당하는 layer만 fine tune** 한다. 
>
> 04. 이때부터 RPN과 Fast R-CNN이 weight를 공유하게 되는데 이번에는 CNN과 RPN은 고정시킨채 **Fast R-CNN에 해당하는 layer만 fine tune** 한다.

## 기존의 방법과 비교

<img src="https://github.com/HwangToeMat/HwangToeMat.github.io/blob/master/Paper-Review/image/FasterRCNN/img4.png?raw=true" style="max-width:100%;margin-left: auto; margin-right: auto; display: block;">

다른 R-CNN계열 모델과 비교해 봤을때 **속도가 월등히 빨라진 것**을 알 수 있다. 이는 Faster R-CNN에서는 기존의 오래걸렸던 **Selective Search 과정을 RPN을 통해 빠르게 진행**하였기 때문이라고 생각할 수 있다.

## Result

<img src="https://github.com/HwangToeMat/HwangToeMat.github.io/blob/master/Paper-Review/image/FasterRCNN/img5.png?raw=true" style="max-width:100%;margin-left: auto; margin-right: auto; display: block;">
