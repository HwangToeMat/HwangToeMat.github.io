---
title: 2. MobileNets 논문 리뷰
image: https://github.com/HwangToeMat/HwangToeMat.github.io/blob/master/Paper-Review/image/MobileNets/img0.png?raw=true
description: >
 MobileNets - MobileNets: Efficient Convolutional Neural Networks for Mobile Vision Applications을 읽고 논문 주요내용을 정리해본다.
author: author1
layout: post
order: 14
---
# [LightWeight DL]  2. MobileNets 논문 리뷰

<a href="https://arxiv.org/pdf/1704.04861.pdf">[PDF] 논문원본</a>

# MobileNets: Efficient Convolutional Neural Networks for Mobile Vision Applications

## 모델 특징

<img src="https://github.com/HwangToeMat/HwangToeMat.github.io/blob/master/Paper-Review/image/MobileNets/img1.png?raw=true" style="max-width:100%;margin-left: auto; margin-right: auto; display: block;">

기존의 모델들은 고성능의 System Resource내에서 높은 정확도를 목표로 설계되어 있었다. 하지만 MobileNet은 그림과 같이 **모바일 기기(낮은 성능의 System Resource)에서도** 충분히 잘 돌아 갈 수 있도록 **적은 연산량**과 **적은 수의 파라미터**를 가지도록 설계 되었다. 이는 딥러닝 모델의 **on-device**화를 가능하게 하도록 하였다. 즉 기존에는 모바일 기기에서 딥러닝 서비스를 "cloud-computing"으로 이용해야 했다면, 이러한 모델을 사용하면 "edge-computing"이 가능하도록 한 것이다.

먼저 이 논문에서 제안한 **주요 아이디어**를 살펴 보면 아래와 같다.

<img src="https://github.com/HwangToeMat/HwangToeMat.github.io/blob/master/Paper-Review/image/MobileNets/img2.png?raw=true" style="max-width:100%;margin-left: auto; margin-right: auto; display: block;">

**기존의 3x3 Conv**의 과정을 3x3 **Depthwise Conv** 와 1x1 **Pointwise Conv**를 사용하여 두번에 걸쳐 진행하였고 이를 통해 **연산량과 파라미터 수를 줄였다.**

<img src="https://github.com/HwangToeMat/HwangToeMat.github.io/blob/master/Paper-Review/image/MobileNets/img3.png?raw=true" style="max-width:100%;margin-left: auto; margin-right: auto; display: block;">

자세히 살펴보면 먼저 **Depthwise Conv**를 통해 각 channel의 정보를 유지하며 **channel별로** Conv를 진행하고 그 다음 **Pointwise Conv**를 사용하여 각 **channel간의 정보를 linear combination**한다. 따라서 결론적으로 기존의 3x3 Conv의 output 크기와 **필요한 정보를 유지**하면서 **연산량은 줄인** 것이다.

## 여러 경우에서의 실험

* Depthwise Separable vs Full Convolution MobileNet(일반적인 Conv)

<img src="https://github.com/HwangToeMat/HwangToeMat.github.io/blob/master/Paper-Review/image/MobileNets/img4_1.png?raw=true" style="max-width:100%;margin-left: auto; margin-right: auto; display: block;">

먼저 일반적인 3x3 Conv를 사용한 모델과 이 논문에서 제안한 방법(Depthwise Separable)을 사용한 모델간의 비교이다. **정확도는 1% 정도 밖에 차이**가 나지 않는 것에 비해 **연산량과 파라미터 수는 압도적으로 줄어든 것**을 볼 수 있다.

* MobileNet Width Multiplier

<img src="https://github.com/HwangToeMat/HwangToeMat.github.io/blob/master/Paper-Review/image/MobileNets/img4_3.png?raw=true" style="max-width:100%;margin-left: auto; margin-right: auto; display: block;">

Width Multiplier는 **모델 내부의 각 layer의 width를 &#945; 만큼의 비율로 줄여** 연산량과 파라미터 수를 줄이는 방법이다. 위의 차트에서 MobileNet 앞의 숫자들(1.0, 0.75, 0.5, 0.25)이 그것이다. &#945;의 값이 클수록 모델은 가벼워지지만 정확도가 낮아진다. 특히 0.5 아래부터는 정확도가 큰폭으로 낮아지는 것을 알 수 있다. 

* MobileNet Resolution Multiplier

<img src="https://github.com/HwangToeMat/HwangToeMat.github.io/blob/master/Paper-Review/image/MobileNets/img4_4.png?raw=true" style="max-width:100%;margin-left: auto; margin-right: auto; display: block;">

Resolution Multiplier는 **모델의 input 이미지의 resolution을 &#961;로 변경 하여** 연산량을 변경시키는 방법이다. 위의 차트에서 MobileNet 뒤의 숫자들(224, 192, 160, 128)이 그것이다. &#961;의 값이 작을수록 모델은 연산량이 줄어들지만 정확도가 낮아진다. input값이 달라진것이기 때문에 파라미터 수는 달라지지 않는다.

## 다양한 task에서 성능 비교

* Classification에서 성능 비교

<img src="https://github.com/HwangToeMat/HwangToeMat.github.io/blob/master/Paper-Review/image/MobileNets/img5.png?raw=true" style="max-width:100%;margin-left: auto; margin-right: auto; display: block;">

* Object Detection에서 성능 비교

<img src="https://github.com/HwangToeMat/HwangToeMat.github.io/blob/master/Paper-Review/image/MobileNets/img6.png?raw=true" style="max-width:100%;margin-left: auto; margin-right: auto; display: block;">

* Face Recognition에서 성능 비교

<img src="https://github.com/HwangToeMat/HwangToeMat.github.io/blob/master/Paper-Review/image/MobileNets/img7.png?raw=true" style="max-width:100%;margin-left: auto; margin-right: auto; display: block;">
