---
title: "(WebRTC) Native Build"
date: 2020-01-22 00:00:00 -0000
---

## depot_tools 설치

```s
$ mkdir depot_tools
$ cd depot_tools
$ git clone https://chromium.googlesource.com/chromium/tools/depot_tools.git
```

---

## 환경변수 설정

`PATH = ~webrtc\depot_tools`

---

## gclient 설치

```s
# 관리자모드 실행
$ gclient
# 자동으로 설치된다.
```

---

## webrtc 다운로드

```s
$ mkdir webrtc-checkout
$ cd webrtc-checkout
$ fetch --nohooks webrtc
$ cd src
$ branch -r
# 최신 버전을 선택
$ git checkout branch-heads/?
$ gclient sync --force
```

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
$ gn gen out\Default
$ ninja -C out/Default
```

> 만약 링크에러가 발생 시

```s
$ gn gen out/Default --args="fatal_linker_warnings=false is_Debug=false"
```

---

* [참고사이트1](https://sourcey.com/articles/building-and-installing-webrtc-on-windows)
* [참고사이트2](https://alnova2.tistory.com/1114)