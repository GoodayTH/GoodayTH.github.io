---
title: "webrtc"
permalink: /webrtc/ # link 직접 지정
toc: true                       # for Sub-title (On this page)
comments: true                  # for disqus Comments
categories:                     # for categories
date: 2020-03-10 00:00:00 -0000
last_modified_at: 2020-03-25 00:00:00 -0000
---

## WebRTC란?

* [WebRTC 이론적 부분](/webrtc/basic/)

---

## 간단한 WebRTC 어플리케이션 만들어보기

* [사전사항](/webrtc/basicapp_00/) : 소스클론 및 개발환경 세팅
* [WebRTC 기초 다지기](/webrtc/basicapp_01/) : nvm 설치 + `getUserMedia`으로 web에서 비디오/오디오 정보 받기
* [WebRTC Signaling 이론](/webrtc/basicapp_02/) : 결국 [WebRTC 이론적 부분](/webrtc/basic/)과 비슷한 설명임.
* [socket.io 사용하기](/webrtc/basicapp_03/)
* [signaling 해보기](/webrtc/basicapp_04/) : `RTCSessionDescription`, `RTCIceCandidate`, `webkitRTCPeerConnection`사용
* []

---

## WebRTC Native

* [WebRTC Native Build](https://goodayth.github.io/webrtc-native-build/)

---

## 기타사항

* [WebRTC ejs, express에 관하여](https://goodayth.github.io/webrtc-ejs-express/)

---

## 미정리

* [WebRTC Signaling 실습(Setting Up Socket.io)](https://goodayth.github.io/webrtc-signaling2/)
* [WebRTC Signaling 실습(Implementing Signaling)](https://goodayth.github.io/webrtc-Implementing-Signaling/) : 설명은 생략, 코드를 살펴보면 됨. - 강의에서도 다른 코드를 보며 자세한 WebRTC Connection과정에 대해 설명하는데 필요할 경우 참고
* [WebRTC For Data Exchange(이론)](https://goodayth.github.io/webrtc-data-exchange/)

> cannot find module 'coffee-script'에 대해서<br>
> package.json 파일에 `"coffee-script": "~1.6.3"` 추가 후 `$ node update`