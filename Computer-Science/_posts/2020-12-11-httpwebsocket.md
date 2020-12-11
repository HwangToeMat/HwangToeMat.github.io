---
title: (웹개발) 05. HTTP와 WebSocket 까지
image: https://github.com/HwangToeMat/HwangToeMat.github.io/blob/master/Computer-Science/image/WEB/HTTP/0.png?raw=true
description: >
 HTTP에서 websocket 까지 발전과정을 살펴보고 어떤곳에서 쓰이는지 알아본다.
author: author1
layout: post
order: 28
---

# [웹개발] 05. HTTP와 WebSocket 까지

## HTTP 란?

인터넷에서 웹서버와 사용자의 인터넷 브라우저 사이에 문서를 전송하기 위해 사용되는 통신 규약을 말한다.
 
HTTP의 중요한 특징인 **Client의 요청이 있을때만** 서버가 응답하여 해당 정보를 제공하면 **연결을 종료**한다는 것이다.
다시 말해 Client가 요청을 보내는 경우에만 서버가 응답하는 단방향적 통신이다.

<img src="https://github.com/HwangToeMat/HwangToeMat.github.io/blob/master/Computer-Science/image/WEB/HTTP/1.jpeg?raw=true" style="max-width:100%;margin-left: auto; margin-right: auto; display: block;">

[이미지 출처](https://hieroglyph.tistory.com/13)

## WebSocket 이란?

브라우저와 웹서버 사이의 통신을 위한 양방향 통신 규격을 말한다.

서버와 Client가 특정 포트를 통해 연결을 성립하고 있어 실시간으로 **양방향 통신**을 하는 방식이다. 서버와 Client 모두 서로에게 요청을 보낼 수 있으며 지속적으로 연결을 유지하는 연결지향형 통신이다. 

<img src="https://github.com/HwangToeMat/HwangToeMat.github.io/blob/master/Computer-Science/image/WEB/HTTP/2.png?raw=true" style="max-width:100%;margin-left: auto; margin-right: auto; display: block;">

[이미지 출처](https://mangkyu.tistory.com/48)

## HTTP와 WebSocket의 특징과 쓰이는 곳

- HTTP

요청이 있을때만 연결이되고 요청을 해결하면 연결이 끊어지는 방식이기 때문에 정적페이지 요청에 사용하면 좋다.
만약, 모든 페이지 요청에 웹소켓을 사용할 경우 이미 데이터를 받은 후에도 계속해서 연결을 유지해야 하기 때문에 부하가 걸리게 된다.
따라서 이럴 경우에는 HTTP가 더 적절하다.

- WebSocket

양방향으로 연결을 유지하는 방식이기 때문에 동적페이지 요청에 사용하면 좋다.
또한 실시간으로 데이터를 주고 받는 주식, 동영상 스트리밍과 같은 상황에서 사용하면 좋다.
