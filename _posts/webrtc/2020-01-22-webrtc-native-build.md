---
title: "(WebRTC) Native Build"
permalink: /webrtc/native_build/ # link 직접 지정
toc: true                       # for Sub-title (On this page)
comments: true                  # for disqus Comments
categories:                     # for categories
date: 2020-01-22 00:00:00 -0000
last_modified_at: 2020-03-18 00:00:00 -0000
sidebar:
  title: "WebRTC 목차"
  nav: webrtc
---

## 사전사항

### python 설치

우선 python 2.7.x가 설치되어 있어야한다.

![](/file/image/webrtc-native-build-image-03.png)

설치시 path지정 잊지말기

### Windows10 SDK 설치

VS Installer에서 설치되는거 보다 홈페이지에서 다운 받는걸 추천<br>
경로의 차이가 있다.

## depot_tools 설치

```s
$ mkdir depot_tools
$ cd depot_tools
$ git clone https://chromium.googlesource.com/chromium/tools/depot_tools.git
$ gclient # webrtc 버전관리도구 설치
```

![](/file/image/webrtc-native-build-image-01.png)

---

## 환경변수 설정

`PATH = ~webrtc\depot_tools\depot_tools`

gclient가 있는 폴더를 PATH에 넣으면 된다.

---

## webrtc 다운로드

```s
$ mkdir webrtc-checkout
$ cd webrtc-checkout
# fetch --nohooks: git의 history는 복사하지 말아달라
# gclient는 checkout도구이고 fetch는 일종의 wrapper라 생각하자
$ fetch --nohooks webrtc
$ cd src
# branch -r : 원격 저장소의 브랜치를 보여달라
$ git branch -r
# 최신 버전을 선택
$ git checkout branch-heads/?
$ gclient sync --force    # 이거 꼭 해야함.
```

![](/file/image/webrtc-native-build-image-02.png)

---

## 빌드

```s
# 환경변수 선언
set DEPOT_TOOLS_WIN_TOOLCHAIN=0
set GYP_MSVS_VERSION=2017
set GYP_GENERATORS=ninja,msvs-ninja
set GYP_DEFINES=component=shared_library target_arch=x64

# in src folder
$ gn gen out/x64/Debug --args="is_debug=true use_rtti=true target_cpu=\"x64\""

# .sln 파일생성
$ gn gen --ide=vs out\Default

# visual studio 자체 빌드가 되지 않기에 빌드는 위에 처럼하거나 아래처럼 간단빌드가능
$ gn gen out/Default --args="fatal_linker_warnings=false is_Debug=false"
$ ninja -C out/Default
```

---

* [참고사이트1](https://sourcey.com/articles/building-and-installing-webrtc-on-windows)
* [참고사이트2](https://alnova2.tistory.com/1114)