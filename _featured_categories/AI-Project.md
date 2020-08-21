---
layout: list
title: AI-Project
slug: AI-Project
description: >
  Carry out various AI projects.
---
# AI-Project

<details>
<summary>See More</summary>
<div markdown="1">
  
## 0. Open-Images_EasyDownload 
Easiest way to get the Data for Deep Learning, by using “Open Images”. <a href="https://github.com/HwangToeMat/Open-Images_EasyDownload">[Helper library for downloading OpenImages categorically.]</a>
![image1](https://github.com/HwangToeMat/Tensorflow-API-HTM/blob/master/0.Open-Images_EasyDownload/image1.png?raw=true)

## 1. Classification <a href="https://github.com/HwangToeMat/Tensorflow-API-HTM/blob/master/1.classification/reCAPTCHA_classification.ipynb">[Break through the reCAPTCHA]</a>
Break through the security program for prevent ing macros, reCAPTCHA , using pretrained model<a href='http://download.tensorflow.org/models/image/imagenet/inception-2015-12-05.tgz'>[Inception_Net]</a>.
As you can see in the picture below, Inception_Net makes it easy to find a bus.
![image1](https://github.com/HwangToeMat/Tensorflow-API-HTM/blob/master/1.classification/image/image0.jpg?raw=true)

## 2. Object_detection <a href="https://github.com/HwangToeMat/Tensorflow-API-HTM/blob/master/2.object_detection">[Football play detection]</a>
We used **ssdlite_mobilenet_v2_coco<a href="http://download.tensorflow.org/models/object_detection/ssdlite_mobilenet_v2_coco_2018_05_09.tar.gz">[Download Link]</a>** to analyze soccer games in real time because we *need fast computing speed.* But as you can see in the image below, our model(Left) performs very well even though it is a lightweight model.
![result3](https://github.com/HwangToeMat/Tensorflow-API-HTM/blob/master/2.object_detection/images/result3.png?raw=true)

## 3. Super-Resolution <a href="https://github.com/HwangToeMat/Asym_VDSR">[Github] Asym_VDSR 코드 원본</a>
**Asymmetric convolution**을 사용하여 기존의 Super-Resolution 모델들의 특징과 성능을 유지하고 **적은 수의 파라미터**로 Super-Resolution 문제를 해결한다. 이 프로젝트에서는 VDSR을 baseline으로 사용하였는데, 기존 VDSR의 구조는 그대로 유지하고 **input, output에 쓰이는 두개의 layer를 제외한 나머지 18개의 layer에 3\*3conv를 3\*1, 1\*3으로 변경**하여 Asym_VDSR을 설계하였다. Asymmetric Convolution을 사용하여 **기존 모델의 구조와 성능은 유지**하면서 연산은 빠르게 할 수 있는 **가벼운 모델로 변경**이 가능했다.
<img src="https://github.com/HwangToeMat/HwangToeMat.github.io/blob/master/AI-Project/image/AsymVDSR/img1.png?raw=true" style="max-width:100%;margin-left: auto; margin-right: auto; display: block;">


## 4. 얼굴인식기반 실시간 교육 플랫폼 개발 - KHUFACE ID <a href="https://github.com/HwangToeMat/FaceRecognition_FlaskServer">[Github] FaceRecognition_FlaskServer 코드 원본</a>
기존 수업에서 이루어지는 문제점을 해결하기위해 딥러닝을 활용하여 얼굴인식기반 실시간 교육 플랫폼(KHUFACE ID)를 개발하였다. 본프로젝트에서 네트워크 설계, 딥러닝모델 설계, 모델 서버 구축, 클라우드 환경설정의 역할을 맡아서 개발하였다.
<img src="https://github.com/HwangToeMat/HwangToeMat.github.io/blob/master/AI-Project/image/KHUFACE/3/video.gif?raw=true" style="max-width:100%;margin-left: auto; margin-right: auto; display: block;">

</div>
</details>
