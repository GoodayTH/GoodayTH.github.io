---
title: "기타사항 정리 페이지 입니다."
permalink: /etc/                # link 직접 지정
toc: true                       # for Sub-title (On this page)
comments: true                  # for disqus Comments
categories:                     # for categories
date: 2020-01-04 00:00:00 -0000
last_modified_at: 2020-05-09 00:00:00 -0000
sidebar:
  title: "etc 목차"
  nav: etc
tag:
  - 기타사항
category:
  - category
excerpt: "기타사항 정리 페이지 입니다"
header:
  teaser: /file/image/etc-page-teaser.gif
  overlay_image: /file/image/main-page.jpg
  overlay_filter: 0.1 # rgba(255, 0, 0, 0.5)
  caption: "Photo credit: [**EBS**](https://ebs.co.kr)"
---

## gradle

* [강의](https://www.youtube.com/watch?v=s-XZ5B15ZJ0&list=PL7mmuO705dG2pdxCYCCJeAgOeuQN1seZz)

* [gradle이란?](/gradle/basic/)
* [설치](/gradle/install/)
* [gradle vs maven](/gradle/gradle-maven/)
* [build](/gradle/build/)
* [task](/gradle/task/)

* [task graph](/gradle/task-graph/)
* [객체](/gradle/object/)
* [파일관리](/gradle/files/)

여기서 부터는 완전히 정리하지 않음 필요없는 부분이 너무 많음 필요할 경우 찾아서 볼 것

* [의존관계](/gradle/dependencies/)

### Example

* [.bat 파일 실행하기](/gradle/example/startbat/)
* [delete file and folder](/gradle/example/delete/)
* [특정 폴더에 파일만 복사하기](/gradle/example/copyfiles/)

### gradle plugin

* [gitpublish](/gradle/plugin/gitpublish/)

---

## Docker

* [Docker file 문법 정리](https://goodayth.github.io/docker-syntax)
* [mac기반 Docker 기본적 사용법](https://goodayth.github.io/docker-mac-basic)
* [Docker WebServer](https://goodayth.github.io/docker-linux-webdav) : WebDav, Transmission(Torrent), Plex Server

---

## Jenkins

* [Windows 기반 MSBuild Jenkins 서버만들기](https://goodayth.github.io/jenkins-windows-msbuild/)
* [Jenkins Window Batch Good Example : MSBuild](/jenkins/windowbatch-goodexample/)
* [Jenkins + gradle plugin](/jenkins/gradleplugin/)
* [Email Notification](/jenkins/emailnoti/)
* [Jenkins WorkSpace에 관해서]() : 간단하기에 글로 정리 - Jenkins가 설치된 폴더의 workspace가 존재 하며 그 폴더에서 git, svn을 clone하여 프로젝트를 빌드한다. 한번씩 헷갈려서 혹시나 해서 적어둠.

---

## Windows Batch

* [*.rc파일 버전 병경하기](/batch/example-file-replace/)

---

## Github.io

* [jekyll로 github page만들기](https://goodayth.github.io/gitpage-make/)
* [테스트 이미지 넣기](/githubio/insert-image/)
* [google analytics 붙이기](https://goodayth.github.io/gitpage-analysis/)
* [google adsense 붙이기](https://goodayth.github.io/gitpage-adsense/)

* [sample-page](https://goodayth.github.io/sample/page-sample/) : sample-page + side-bar navigator
* [sitemap 넣기](/github-io/insert-sitemap/)

---

## Git

* [Git 명령어 정리](/git/command-summary/)
    
* [git의 difftool 지정하기(beyond compare4)](https://goodayth.github.io/git-difftool/)
* [Sourcetree로 Git 정리하기](https://goodayth.github.io/git-source-tree/)
* [master, develop, hofix 등 git flow 정리](https://goodayth.github.io/git-flow/)
* [Sourcetree로 cherry pick하기](https://goodayth.github.io/git-cherry-pick/)
* [과거 commit 버전간 비교](https://goodayth.github.io/git-compare-past-commit/)

* [sourcetree이용 스태시와 특정 커밋 비교](/git/stash-compare/)

---

## markdown

* [markdown 문법](/markdown/grammer/)

---

## Windows command

* [Window 명령어 정리](/windows/command/)

* [인바운드, 아웃바운드 규칙이란](/windows/inoutbound/)

---

## Visual Studio

* [DLL 디버깅 (Break Point 찍기)](/vs/dll-debug/)
* [각종 설정](/vs/settings/)
* [WinDbg 사용하기](/vs/WinDbg/)

---

## curl

* [설치](/curl/install/)

---

## websocket

* [참고사이트](http://utk-unm.blogspot.com/2016/10/websocket.html)

* WebSocket
    - Transport protocol 일종(Real-time web application을 지원(서버와 실시간 통신지원))
    - Web의 TCP Socket이라 생각하자

* 대표적 사용예
    - 구글 Doc과 같이 여러명 동시 수정 웹
    - 실시간 스포츠 업데이트 사이트

---

## stomp

Simple (or Streaming) Text Orientated Messaging Protocol.<br>
말 그대로 메시징 프로토콜이다.<br>
websocket에서 사용되며 특정 규약에 맞춰 보낼시 파싱<br>

* [참고사이트](https://swiftymind.tistory.com/tag/Websocket%20%2B%20STOMP)

---

## powershell 7

* [GitHub(다운로드)](https://github.com/PowerShell/PowerShell/releases)

