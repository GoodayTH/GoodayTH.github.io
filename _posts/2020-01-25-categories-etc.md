---
title: "etc 목차"
permalink: /etc/                # link 직접 지정
toc: true                       # for Sub-title (On this page)
comments: true                  # for disqus Comments
categories:                     # for categories
date: 2020-01-04 00:00:00 -0000
last_modified_at: 2020-03-22 00:00:00 -0000
sidebar:
  title: "etc 목차"
  nav: etc
---

## Docker

* [Docker file 문법 정리](https://goodayth.github.io/docker-syntax)
* [mac기반 Docker 기본적 사용법](https://goodayth.github.io/docker-mac-basic)
* [Docker WebServer](https://goodayth.github.io/docker-linux-webdav) : WebDav, Transmission(Torrent), Plex Server

---

## Jenkins

* [Windows 기반 MSBuild Jenkins 서버만들기](https://goodayth.github.io/jenkins-windows-msbuild/)

---

## Github.io

* [jekyll로 github page만들기](https://goodayth.github.io/gitpage-make/)
* [테스트 이미지 넣기]()

```s
![이미지](/file/image/test_image.png)
```

> Example

![](/file/image/test_image.png)

* [google analytics 붙이기](https://goodayth.github.io/gitpage-analysis/)
* [google adsense 붙이기](https://goodayth.github.io/gitpage-adsense/)
* [sample-page](https://goodayth.github.io/sample/page-sample/) : sample-page + side-bar navigator

---

## Git

* [git의 difftool 지정하기(beyond compare4)](https://goodayth.github.io/git-difftool/)
* [Sourcetree로 Git 정리하기](https://goodayth.github.io/git-source-tree/)
* [master, develop, hofix 등 git flow 정리](https://goodayth.github.io/git-flow/)
* [Sourcetree로 cherry pick하기](https://goodayth.github.io/git-cherry-pick/)
* [과거 commit 버전간 비교](https://goodayth.github.io/git-compare-past-commit/)
* [sourcetree이용 스태시와 특정 커밋 비교](/git/stash-compare/)

**fetch --nohooks 명령**

git history를 복사하지 않음

**git branch -r 명령**

* 일단 branch는 브랜치를 보는 명령이고
* -r : 원격 저장소 branch의 리스트를본다.
* -a : 로컬, 원격 모든 저장소의 branch를 본다.

> * [참고사이트](https://cjh5414.github.io/get-git-remote-branch/)

**특정 tag clone 하기**

```s
$ git clone -b <tag> <url>
# example
$ git clone -b v1.0 git://github.com/source
```

**현재 git 상태 확인 밑 모든파일 스태이지 올리기**

```s
$ git status
```

![](/file/image/git_status.png)

```s
$ git add *
```

![](/file/image/git_status2.png)

---

## markdown

**(markdown) 링크 찾아가기**

```s
[네임](#링크명)
```

위와 같이 링크를 걸면 링크로 들어가는데<br>
현재 io에서 링크명을 대문자 영어로 넣으면 링크를 못 찾아감<br>

아래와 같이 넣을 것!<br>

```s
[네임](#링크명(소문자))
```

---

## Window

**윈도우 버전확인** 

```s
# cmd
$ winver
```

![](/file/image/winver.png)

**인바운드, 아웃바운드 규칙**

고급 방화벽에서 확인할 수 있다.

![](/file/image/win-firewall.PNG)

* 인바운드 규칙
    - 외부(인터넷)에서 내부(내 PC)로 들어오는 규칙
    - Windows의 기본 인바운드 규칙이 모든접속 **차단**이기에 추가되는 규칙은 보통 새로운 포트를 추가할때 사용된다.
* 아웃바운드 규칙
    - 내부(내 PC)에서 외부(인터넷)로 규칙
    - Windows의 기본 아웃바운드 규직이 모든접속 **허용**이기에 추가되는 경우는 특정 포트를 사용해야하는 경우 추가되어 사용된다.

> * [참고사이트](https://kcmschool.com/77)

---

## Visual Studio

**DLL 디버깅하기 (Break Point 찍기)**

이게 참.. 말로 설명하기 힘든데 말로 설명을 해야함... 그렇기에 이해가 잘 되지 않더라도 다시 잘 읽어보며 해보면 될 것...

우선 두 개의 프로젝트가 존재한다.<br>
1. DLL 프로젝트<br>
2. DLL 을 사용할 exe를 생성하는 프로젝트<br>

우선, DLL 프로젝트에서 다음과 같은 절차를 수행한다.<br>
속성 -> 디버깅 -> 명령 인수에 빌드한 *.dll이 아닌 사용될(exe 바이너리에서 실행할) *.dll이 있는 폴더의 위치를 넣는다.

![](/file/image/VS_DLL_Debug_Image_01.png)

다음, DLL을 사용할 프로젝트에서 다음과 같은 절차를 수행한다.<br>
릴리즈 바이너리 생성 -> (여기서 주의할 점은 VisualStudio로 바이너리를 실행하면 안됨, 하나의 바이너리에 두 개의 디버거를 붙일 수 없기때문이다.) -> 릴리즈 바이너리 실행

다음, DLL프로젝트에서 다음과 같은 절차를 수행<br>
목록 -> 디버그 -> 프로세스에 연결 -> 실행중인 프로세스를 선택 -> 실행한 바이너리 선택

![](/file/image/VS_DLL_Debug_Image_02.png)

---

**Visual Studio 자동 서식변경 설정**

옵션 -> 텍스트 편집기 -> C/C++ -> 서식 -> 일반

![](/file/image/VS_Text_edit_Image_01.png)

---

**WinDbg 사용하기**

```s
.ecxr       # 문제가 발생했던 당시의 레지스터를 보여준다.
```

아래 예시 그림은 문제가 없는 프로그램을 덤프했기에 별도로 문제가 안보임

![](/file/image/windbg-image-01.png)

```s
k           # 콜 스택 출력
```

![](/file/image/windbg-image-02.png)

```s
lmvm SO_Server      # 모듈정보 출력
# 위 명령보다 lm이 훨씬 간결하게 보여준다.
lm
```

많이 나오는데 아래만 보면 됨.<br>
흠... 원래 pdb가 연결이 안돼있어야 하는데 연결이 되어 있군... -> 아마 디버그 모드로 실행해서그런듯.. 다시 만들어 보자.

```
00007ff6`ec120000 00007ff6`ec17b000   MFCApplication1 C (pdb symbols)          C:\ProgramData\dbg\sym\MFCApplication1.pdb\CF4493EAB56C4BB698F44456D1DB8D2D1\MFCApplication1.pdb
    Loaded symbol image file: MFCApplication1.exe
    Image path: C:\Users\taehy\source\repos\MFCApplication1\x64\Debug\MFCApplication1.exe
    Image name: MFCApplication1.exe
```

릴리즈로 로드하니 심볼을 찾지못했다.

```
00007ff7`ce8e0000 00007ff7`ce8fd000   MFCApplication1   (deferred)             
    Image path: C:\Users\taehy\source\repos\MFCApplication1\x64\Release\MFCApplication1.exe
    Image name: MFCApplication1.exe
```

```s
.symfix c:\OsSymbols        # 운영체제 심볼 맞추기
```

`c:\OsSymbols`로 운영체제의 심볼파일을 로드한다.<br>

![](/file/image/windbg-image-03.png)

```s
.sympath+ c:\<symbol경로>     # symbol의 경로 입력
```

symbol의 경로에는 pdb, exe파일이 있어야한다.

![](/file/image/windbg-image-04.png)

![](/file/image/windbg-image-05.png)

```s
.reload
```

심볼파일(pdb)를 잘 로드했는지 확인

```s
#lmvm SO_Server
lm
```

다시 콜 스택 출력해본다.

```s
k
```

![](/file/image/windbg-image-06.png)

> * [참고사이트](http://heart4u.co.kr/tblog/411)

---

## curl

> * [참고사이트](https://m.blog.naver.com/javaking75/220776461230)

* command URL : 명령어 기반 URL 접근가능하게 해주는 툴이다.
* 다운로드는 [여기](https://curl.haxx.se/download.html)서 혹은 [여기](https://curl.haxx.se/windows/) 하자

![](/file/image/curl_image_01.png)

받아서 압축을 풀어보면 bin폴더 내에 curl.exe가 있다.<br>
커맨드 라인을 열어서 아래 명령어를 입력해본다.

```s
$ curl https://goodayth.github.io
```

![](/file/image/curl_image_02.png)

---

## websocket

> * [참고사이트](http://utk-unm.blogspot.com/2016/10/websocket.html)

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

> * [참고사이트](https://swiftymind.tistory.com/tag/Websocket%20%2B%20STOMP)

---

## powershell 7

* [GitHub(다운로드)](https://github.com/PowerShell/PowerShell/releases)

