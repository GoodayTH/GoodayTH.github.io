---
title: "webrtc : janus - Janus Server 설치"
permalink: webrtc/janus/install/                # link 직접 지정
comments: true                  # for disqus Comments
categories:                     # for categories
date: 2020-06-12 00:00:00 -0000
last_modified_at: 2020-06-12 00:00:00 -0000
sidebar:
  title: "webrtc 목차"
  nav: webrtc
tag:
  - webrtc
  - janus
category:
  - install
excerpt: ""
header:
  teaser: /file/image/webrtc-page-teaser.gif
---

* [참고사이트](https://github.com/meetecho/janus-gateway)

```s
$ sudo apt-get install git
$ sudo apt-get install aptitude
$ sudo apt-get install meson
```

```s
$ sudo -i
$ aptitude install libmicrohttpd-dev libjansson-dev \
	libssl-dev libsrtp-dev libsofia-sip-ua-dev libglib2.0-dev \
	libopus-dev libogg-dev libcurl4-openssl-dev liblua5.3-dev \
	libconfig-dev pkg-config gengetopt libtool automake
```