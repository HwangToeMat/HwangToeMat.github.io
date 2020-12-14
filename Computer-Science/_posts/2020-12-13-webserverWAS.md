---
title: (웹개발) 06. WebServer와 WAS의 개념
image: https://github.com/HwangToeMat/HwangToeMat.github.io/blob/master/Computer-Science/image/WEB/WAS/0.png?raw=true
description: >
 WebServer와 WAS의 개념을 살펴보고 어떤곳에서 쓰이는지 알아본다.
author: author1
layout: post
order: 29
---

# [웹개발] 06. WebServer와 WAS의 개념과 역할

## 개발한 웹을 배포할때 주로 사용하는 구조

<img src="https://github.com/HwangToeMat/HwangToeMat.github.io/blob/master/Computer-Science/image/WEB/WAS/1.png?raw=true" style="max-width:100%;margin-left: auto; margin-right: auto; display: block;">

[이미지 출처](https://hackernoon.com/a-guide-to-scaling-machine-learning-models-in-production-aa8831163846)

최근에 Flask를 자주 사용하는데 개발한 웹을 배포할때 간단한 구조는 위와같다. 그림에서 nginx는 WebServer의 역할을 하고, uWSGI는 WAS의 역할을 한다.
이 두가지 역할을 통해 Client의 요청에 맞게 Flask로 구현된 서비스를 연결하여 DB에서 필요한 정보를 가공하여 제공할 수 있는 것이다.

여기서 WebServer와 WAS가 각각 어떤역할을 하고 왜 존재하는지 알아보도록 하겠다.

## WebServer의 개념 및 역할?

웹서버는 클라이언트로부터 HTTP 요청을 받아 필요한 데이터를 제공하는 역할을 한다.
이때 웹서버는 주로 정적인 컨텐츠를 제공하고 동적인 컨텐츠에 대한 요청을 WAS로 전달하여 처리된 결과를 클라이언트에게 반환한다.

웹서버는 주로 nginx와 aparch, iis가 많이 쓰이는데, 최근에는 쓰레드개념인 다른 웹서버에비해 Event-Driven구조를 사용하는 nginx를 많이 사용한다.

## WAS의 개념 및 역할?

WAS는 전달받은 동적컨텐츠에대한 요청을 처리하여 제공하는 역할을 하는 미들웨어이다.
이때 앞에서 요청받은 HTTP 요청을 앱에 맞게 변환하여 전달하고 처리된 값을 웹서버에 맞게 변환하여 전달해주는 역할을 한다.

WAS는 주로 Tomcat, uWsgi, gUnicorn 등이 있다.

