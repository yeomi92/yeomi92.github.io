---
layout: post
title: "Ajax"
subtitle: "javascript"
date: 2020-10-11 -0400
background: "/img/posts/06.jpg"
category: "javascript"
---

ajax(Asynchronous Javascript And Xml)는 javascript 라이브러리 중의 하나

브라우저가 가지고 있는 XMLHttpRequest 객체를 이용해서 전체 페이지가 아닌 페이지의 일부만 데이터를 로드하는 기법.

즉 Javascript를 사용한 비동기 통신, 클라이언트와 서버간에 XML 데이터를 주고받는 기술이다.

\* 비동기 방식이란 웹페이지를 리로드하지 않고 데이터를 불러오는 방식

#### 장점

1\. 웹페이지 속도 향상

2\. 서버의 처리가 완료될 때까지 기다리지 않고 처리 가능

3\. 서버에서 Data만 전송하면 됨

4\. 다양한 UI 가능(페이지 전체 리로드가 아니기 때문에)

#### 단점

1\. 히스토리 관리 안됨

2\. 연속된 데이터 요청으로 서버 부하 증가할 수 있음

3\. XMLHttpRequest를 통해 통신하는 경우 사용자에게 진행 정보가 주어지지않음