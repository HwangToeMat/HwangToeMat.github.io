---
title: 1. SQUEEZENET 논문 리뷰
image: https://github.com/HwangToeMat/HwangToeMat.github.io/blob/master/Paper-Review/image/SQUEEZENET/img0.png?raw=true
description: >
 SQUEEZENET - SQUEEZENET: ALEXNET-LEVEL ACCURACY WITH 50X FEWER PARAMETERS AND <0.5MB MODEL SIZE을 읽고 논문 주요내용을 정리해본다.
author: author1
layout: post
order: 13
---
# [LightWeight DL]  1. SQUEEZENET 논문 리뷰

<a href="https://arxiv.org/pdf/1602.07360.pdf">[PDF] 논문원본</a>

# SQUEEZENET: ALEXNET-LEVEL ACCURACY WITH 50X FEWER PARAMETERS AND <0.5MB MODEL SIZE

## 모델 특징

<img src="https://github.com/HwangToeMat/HwangToeMat.github.io/blob/master/Paper-Review/image/SQUEEZENET/img1.png?raw=true" style="max-width:100%;margin-left: auto; margin-right: auto; display: block;">

기존의 모델들은 고성능의 System Resource내에서 높은 정확도를 목표로 설계되어 있었다. 특히 이 논문의 대조군인 AlexNet은 classification에서 높은 정확도를 보여줬지만 모델이 너무 무거워 낮은 성능의 System Resource에서는 사용하기 어려웠다.

하지만 SQUEEZENET은 그림과 같이 오렌지에서 즙을 짜는것(SQUEEZE)처럼 **기존 모델의 성능을 유지하면서 용량과 파라미터 수는 줄이도록** 설계하였다. 이 논문에서 개인적으로 제일 마음에 드는 부분은 제목이다.

**ALEXNET-LEVEL ACCURACY WITH 50X FEWER PARAMETERS AND <0.5MB MODEL SIZE**

~~기존의 모델(AlexNet)과 같은 정확도이면서 파라미터 수를 50배나 줄였고 용량을 0.5MB이하로 줄였다고 당당히 말하는 것이 너무 멋있는것 같다. ㅎㅎ~~

먼저 이 논문에서 제안한 **주요 아이디어**를 살펴 보면 아래와 같다.

### Fire Module

<img src="https://github.com/HwangToeMat/HwangToeMat.github.io/blob/master/Paper-Review/image/SQUEEZENET/img2.png?raw=true" style="max-width:100%;margin-left: auto; margin-right: auto; display: block;">

이 논문에서 제안한 Fire Module은 그림에서와 같이 Squeeze layer와 Expand layer로 이루어져 있다.

**Squeeze layer**는 **1x1 Conv**로 이루어져 있다. 이는 각 채널간의 정보를 **linear combination하는 Pointwise Conv의 역할**을 진행한다. 이 부분에서 **모델의 용량과 파라미터를 수를 줄여주는 과정**이 일어난다. 

**Expand layer**는 **1x1 Conv**와 **3x3 Conv**로 이루어져 있다. **모델을 가볍게 해줄 수** 있지만 feature extraction을 잘 하지 못하는 **1x1 Conv**와 **feature extraction을 잘**하지만 모델을 무겁게 하는 **3x3 Conv**이 **상호 보완적관계**로 같이 쓰이는 것이다. 이때 파라미터 값을 조절하여 1x1 Conv와 3x3 Conv의 수를 조절할 수 있다.  

### Vanilla vs Simple bypass vs Complex bypass

<img src="https://github.com/HwangToeMat/HwangToeMat.github.io/blob/master/Paper-Review/image/SQUEEZENET/img3.png?raw=true" style="max-width:100%;margin-left: auto; margin-right: auto; display: block;">

<img src="https://github.com/HwangToeMat/HwangToeMat.github.io/blob/master/Paper-Review/image/SQUEEZENET/img4.png?raw=true" style="max-width:100%;margin-left: auto; margin-right: auto; display: block;">

### Squeeze ratio(SR) & Percentage of 3x3 filters in expand layers

<img src="https://github.com/HwangToeMat/HwangToeMat.github.io/blob/master/Paper-Review/image/SQUEEZENET/img5.png?raw=true" style="max-width:100%;margin-left: auto; margin-right: auto; display: block;">

## Result

<img src="https://github.com/HwangToeMat/HwangToeMat.github.io/blob/master/Paper-Review/image/SQUEEZENET/img6.png?raw=true" style="max-width:100%;margin-left: auto; margin-right: auto; display: block;">
