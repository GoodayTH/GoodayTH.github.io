---
title: "webrtc 목차"
permalink: /webrtc/                # link 직접 지정
toc: true                       # for Sub-title (On this page)
comments: true                  # for disqus Comments
categories:                     # for categories
date: 2020-03-10 00:00:00 -0000
last_modified_at: 2020-03-16 00:00:00 -0000
sidebar:
  title: "webrtc 목차"
  nav: webrtc
---

## WebRTC란?

* [WebRTC 이론적 부분](/webrtc/basic/)

---

## 간단한 WebRTC 어플리케이션 만들어보기 - basicapp

* [사전사항](/webrtc/basicapp_00/) : 소스클론 및 개발환경 세팅
* [WebRTC 기초 다지기](/webrtc/basicapp_01/) : nvm 설치 + `getUserMedia`으로 web에서 비디오/오디오 정보 받기
* [WebRTC Signaling 이론](/webrtc/basicapp_02/) : 결국 [WebRTC 이론적 부분](/webrtc/basic/)과 비슷한 설명임.
* [socket.io 사용하기](/webrtc/basicapp_03/)
* [signaling 해보기](/webrtc/basicapp_04/) : `RTCSessionDescription`, `RTCIceCandidate`, `webkitRTCPeerConnection`사용
* [data channel 사용해보기](/webrtc/basicapp_05/) : 

나머지 사항은 Example인데 더 깊게 학습이 필요할 경우 진행할 것.

### 정리가 안되는거 같아서 중요한 부분만 정리한다.

우선 통신은 다음과 같은 방식으로 진행된다.

1. Fetching - getUserMedia를 이용 사용자의 영상/음성 정보를 가져온다.

```js
function startStream() {
navigator.getUserMedia = navigator.getUserMedia || navigator.webkitGetUserMedia || navigator.mozGetUserMedia;
// ...

navigator.getUserMedia(constraints, onSuccess, onError);
}
```

2. (추가) Signaling Server 접속을 위한 io사용법

* 송신 : `app.io.room(req.data).broadcast()`
* 수신 : `io.on()`
* Signal : `io.emit()` -> slot : `app.io.route()`

```js
var express = require('express.io');
var app = express();
app.http().io();

// ...

app.io.route('ready', function(req) {
	req.io.join(req.data)
	app.io.room(req.data).broadcast('announce', {   // 상대방의 announce로 메시지 송신
		message: 'New client in the ' + req.data + ' room.'
	})
})

app.io.route('send', function(req) {
    app.io.room(req.data.room).broadcast('message', {
        message: req.data.message,
		author: req.data.author
    });
})

// ...

io = io.connect();
io.emit('ready', ROOM);   // io.route('read')로 signal을 보낸다.

io.on('announce', function(data) {  // announce메시지 수신 
  displayMessage(data.message);
});

io.on('message', function(data) {
  displayMessage(data.author + ": " + data.message);
});

sendMessage.addEventListener('click', function(ev){
  io.emit('send', {"author":myName.value, "message":myMessage.value, "room":ROOM});
  ev.preventDefault();
}, false);
```

3. Signaling - Client측에서 Signaling Server에 접속하여 통신하고자 하는 Client의 정보를 받는다.

* webkitRTCPeerConnection : Signal Server에게 내 정보를 송신(Offer SDP)
* RTCSessionDescription : 상대방의 정보를 수신 (Receive SDP)
* RTCIceCandidate : 후보군 정보를 수신

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