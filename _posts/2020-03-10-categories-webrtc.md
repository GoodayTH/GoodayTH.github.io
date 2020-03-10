---
title: "webrtc"
permalink: /webrtc/ # link 직접 지정
toc: true                       # for Sub-title (On this page)
comments: true                  # for disqus Comments
categories:                     # for categories
date: 2020-03-10 00:00:00 -0000
last_modified_at: 2020-03-25 00:00:00 -0000
---

> * [Example Github](https://github.com/GoodayTH/webrtc-js-example)<br>
> 단순 Clone해서 사용하면 안됨, <br>
> `$ npm show <module name> version` 명령을 통해 자신의 버전과 맞게 package.json를 수정<br>
> 추가해야하는 모듈은 : coffee-script, connect 두 개이다.<br>
> ![](/file/image/webrtc_Image_01.png)<br>
> node_module폴더는 삭제 후 `$ npm install` 진행<br>

* [WebRTC Native Build](https://goodayth.github.io/webrtc-native-build/)

* [WebRTC ejs, express에 관하여](https://goodayth.github.io/webrtc-ejs-express/)

> 아래 실습과제를 수행하기 위해서 ...<br>
> package.json을 상황에 맞게 수정해야함.<br>
>
> ```s
> $ npm show ejs version
> $ npm show express.io version
> $ npm show express version
> ```
>
> 확인 후
>
> ```json
> {
> 	"name": "intro-webrtc",
> 	"version": "0.0.1",
> 	"private": true,
> 	"dependencies": {
> 		"coffee-script": "^1.12.7",
> 		"connect": "3.x",
> 		"ejs": "3.x",
> 		"express": "4.x",
> 		"express.io": "1.x"
> 	}
> }
> ```
>
> package.json 수정 후 `$ npm install` 수행
>
> 설치가 된다면 `$ node server` 실행

* [WebRTC 기초 다지기](https://goodayth.github.io/webrtc-basic/)
* [WebRTC Signaling 이론](https://goodayth.github.io/webrtc-signaling/)
* [WebRTC Signaling 실습(Setting Up Socket.io)](https://goodayth.github.io/webrtc-signaling2/)
* [WebRTC Signaling 실습(Implementing Signaling)](https://goodayth.github.io/webrtc-Implementing-Signaling/) : 설명은 생략, 코드를 살펴보면 됨. - 강의에서도 다른 코드를 보며 자세한 WebRTC Connection과정에 대해 설명하는데 필요할 경우 참고
* [WebRTC For Data Exchange(이론)](https://goodayth.github.io/webrtc-data-exchange/)

> cannot find module 'coffee-script'에 대해서<br>
> package.json 파일에 `"coffee-script": "~1.6.3"` 추가 후 `$ node update`

