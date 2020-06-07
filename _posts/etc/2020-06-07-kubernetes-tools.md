---
title: "Kubernetes : Kubernetes 도구활용"
permalink: kubernetes/tools/                # link 직접 지정
toc: true                       # for Sub-title (On this page)
comments: true                  # for disqus Comments
categories:                     # for categories
date: 2020-06-07 00:00:00 -0000
last_modified_at: 2020-06-07 00:00:00 -0000
sidebar:
  title: "etc"
  nav: etc
excerpt: ""
tag:
  - Kubernetes
category:
  - tools
header:
  teaser: /file/image/etc-page-teaser.gif
---

> 다양한 tool이 존재하지만 예제에는 구글 쿠버네티스를 활용할 예정(아마존, 마이크로소프트 모두 이런 툴을 제공한다.)

* [구글 쿠버네티스 엔진](https://cloud.google.com/kubernetes-engine)

> 이게 이상한게 우리나라 ip에서는 접속이 안될때가 있음 vpn을 통해서 다른 나라 ip를 통해 접속해서 가입하자

클러스터 만들기

![](/file/image/kubernetes-tools-01.png)

다른건 다 그대로 두고 부팅 디스크만 변경하면 된다.

![](/file/image/kubernetes-tools-02.png)

![](/file/image/kubernetes-tools-03.png)

이렇게 똑같이 3개 더 만든다.

![](/file/image/kubernetes-tools-04.png)

참고로 예제는 VM instance-01에서 02, 03, 04로 접근할 수 있도록 만들 것이다.<br>

우선 VM instance-01의 ssh에 접근해보자.

![](/file/image/kubernetes-tools-05.png)

![](/file/image/kubernetes-tools-06.png)

ssh키를 생성

```s
$ ssh-keygen -t rsa
```

잘 생성되었는지 확인

```s
$ ls -al .ssh/
```

![](/file/image/kubernetes-tools-07.png)

파일이 보인다면 생성완료<br>

공개키의 내용을 복사해둔다.

```s
$ cat .ssh/id_rsa.pub
```

위에 나온 내용을 별도로 복사해 둔다.

![](/file/image/kubernetes-tools-08.png)

ssh를 넣는다

