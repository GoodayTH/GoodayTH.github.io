---
title: "(WebRTC) Client Server Example"
permalink: opens/webrtc/cs-example/                # link 직접 지정
#toc: true                       # for Sub-title (On this page)
comments: true                  # for disqus Comments
categories:                     # for categories
date: 2020-10-02 00:00:00 -0000
last_modified_at: 2020-10-02 00:00:00 -0000
tag:
  - OpenSource
  - WebRTC
category:
  - Example
sidebar:
  - title: ""
  - nav:
classes: wide
excerpt: ""
header:
  teaser: /file/image/OpenS-page-teaser.gif
---

* [Get Code](https://github.com/EasyCoding-7/webrtc-example)

## Client

### Class UML

![](/file/image/cs-example-1.png)

### WebRTC 통신

함수 호출 순서

```s
# 생성
Conductor::Conductor

# 로그인
Conductor::StartLogin
Conductor::OnMessageSent
Conductor::OnSignedIn
Conductor::UIThreadCallback

# Peer 확인
Conductor::OnPeerConnected

# Peer 연결
Conductor::ConnectToPeer
Conductor::InitializePeerConnection
Conductor::CreatePeerConnection
Conductor::AddTracks
Conductor::OnSuccess
Conductor::SendMessage
Conductor::UIThreadCallback
Conductor::OnMessageSent
Conductor::OnIceCandidate
Conductor::SendMessage
Conductor::OnIceCandidate
Conductor::SendMessage
Conductor::OnIceCandidate
Conductor::SendMessage
Conductor::UIThreadCallback
Conductor::OnIceCandidate
Conductor::SendMessage
Conductor::OnIceCandidate
Conductor::SendMessage
Conductor::UIThreadCallback
Conductor::UIThreadCallback
Conductor::UIThreadCallback
Conductor::OnIceCandidate
Conductor::SendMessage
Conductor::UIThreadCallback
Conductor::UIThreadCallback
Conductor::UIThreadCallback
Conductor::OnMessageSent
Conductor::UIThreadCallback
Conductor::OnMessageSent
Conductor::UIThreadCallback
Conductor::OnMessageSent
Conductor::UIThreadCallback
Conductor::OnIceCandidate
Conductor::SendMessage
Conductor::UIThreadCallback
Conductor::OnMessageSent
Conductor::OnIceCandidate
Conductor::SendMessage
Conductor::UIThreadCallback
Conductor::UIThreadCallback
Conductor::OnIceCandidate
Conductor::SendMessage
Conductor::OnIceCandidate
Conductor::SendMessage
Conductor::OnIceCandidate
Conductor::SendMessage
Conductor::UIThreadCallback
Conductor::OnIceCandidate
Conductor::SendMessage
Conductor::OnIceCandidate
Conductor::SendMessage
Conductor::OnIceCandidate
Conductor::SendMessage
Conductor::UIThreadCallback
Conductor::UIThreadCallback
Conductor::OnMessageSent
Conductor::UIThreadCallback
Conductor::UIThreadCallback
Conductor::UIThreadCallback
Conductor::UIThreadCallback
Conductor::OnMessageSent
Conductor::UIThreadCallback
Conductor::OnMessageSent
Conductor::UIThreadCallback
Conductor::OnMessageSent
Conductor::UIThreadCallback
Conductor::OnMessageSent
Conductor::UIThreadCallback
Conductor::OnMessageSent
Conductor::UIThreadCallback
Conductor::OnMessageSent
Conductor::UIThreadCallback
Conductor::OnMessageSent
Conductor::UIThreadCallback
Conductor::OnMessageSent
Conductor::UIThreadCallback
Conductor::OnMessageSent
Conductor::UIThreadCallback
Conductor::OnMessageFromPeer
Conductor::OnAddTrack
Conductor::OnAddTrack
Conductor::UIThreadCallback
Conductor::UIThreadCallback
Conductor::OnMessageFromPeer
Conductor::OnMessageFromPeer
Conductor::OnMessageFromPeer
```

---

## Server