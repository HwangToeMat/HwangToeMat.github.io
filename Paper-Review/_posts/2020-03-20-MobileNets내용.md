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


<img src="https://github.com/HwangToeMat/HwangToeMat.github.io/blob/master/Paper-Review/image/MobileNets/img2.png?raw=true" style="max-width:100%;margin-left: auto; margin-right: auto; display: block;">

<img src="https://github.com/HwangToeMat/HwangToeMat.github.io/blob/master/Paper-Review/image/MobileNets/img3.png?raw=true" style="max-width:100%;margin-left: auto; margin-right: auto; display: block;">

<img src="https://github.com/HwangToeMat/HwangToeMat.github.io/blob/master/Paper-Review/image/MobileNets/img4_1.png?raw=true" style="max-width:100%;margin-left: auto; margin-right: auto; display: block;">

<img src="https://github.com/HwangToeMat/HwangToeMat.github.io/blob/master/Paper-Review/image/MobileNets/img4_2.png?raw=true" style="max-width:100%;margin-left: auto; margin-right: auto; display: block;">

<img src="https://github.com/HwangToeMat/HwangToeMat.github.io/blob/master/Paper-Review/image/MobileNets/img4_3.png?raw=true" style="max-width:100%;margin-left: auto; margin-right: auto; display: block;">

<img src="https://github.com/HwangToeMat/HwangToeMat.github.io/blob/master/Paper-Review/image/MobileNets/img4_4.png?raw=true" style="max-width:100%;margin-left: auto; margin-right: auto; display: block;">

## Result

* Classification에서 성능 비교

<img src="https://github.com/HwangToeMat/HwangToeMat.github.io/blob/master/Paper-Review/image/MobileNets/img5.png?raw=true" style="max-width:100%;margin-left: auto; margin-right: auto; display: block;">

* Object Detection에서 성능 비교

<img src="https://github.com/HwangToeMat/HwangToeMat.github.io/blob/master/Paper-Review/image/MobileNets/img6.png?raw=true" style="max-width:100%;margin-left: auto; margin-right: auto; display: block;">

* Face Recognition에서 성능 비교

<img src="https://github.com/HwangToeMat/HwangToeMat.github.io/blob/master/Paper-Review/image/MobileNets/img7.png?raw=true" style="max-width:100%;margin-left: auto; margin-right: auto; display: block;">
