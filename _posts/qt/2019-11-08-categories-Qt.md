---
title: "Qt"
permalink: qt/                # link 직접 지정
#toc: true                       # for Sub-title (On this page)
comments: true                  # for disqus Comments
categories:                     # for categories
date: 2020-03-15 00:00:00 -0000
last_modified_at: 2020-05-09 00:00:00 -0000
sidebar:
  title: "Qt"
  nav: qt
tag:
  - qt
category:
  - category
classes: wide
excerpt: "Qt와 관련된 지식을 정리한 홈페이지 입니다."
header:
  teaser: /file/image/qt-page-teaser.gif
  overlay_image: /file/image/main-page.jpg
  overlay_filter: 0.1 # rgba(255, 0, 0, 0.5)
  caption: "Photo credit: [**EBS**](https://ebs.co.kr)"
  actions:
    - label: "Qt HomePage"
      url: "https://www.qt.io/"
---

## Multi-Threading, IPC

우선 Qt Thread에 대해 잘 모른다면 아래의 Thread를 먼저 읽어보자.

* [Get Code](https://github.com/EasyCoding-7/Qt-MultiThread-IPC-Example)

* [Create Thread](/qt/mthread-ipc/create-thread/)
* [Move To Thread](/qt/mthread-ipc/move-to-thread/)
* [Subclass QThread](/qt/mthread-ipc/subclass-thread/)

* [QThread asynchronous(Create Thread)](/qt/mthread-ipc/a-create-thread/)
* [QThread asynchronous(Move To Thread)](/qt/mthread-ipc/a-move-to-thread/)
* [QThread asynchronous(Subclass QThread)](/qt/mthread-ipc/a-subclass-thread/)

* [ThreadPool and QRunnuable](/qt/mthread-ipc/threadpool-runnable/)

## Thread

> * [Qt Thread](/qt/thread/)

* [Q. std thread냐 QThread냐?]() : 
  - Thread - 1의 waitcondition예제를 보면 알겠지만 Signal and Slot의 처리에 있어 QThread가 유리하다, manager에서 Thread의 함수 호출을 쉽게 할 수 있다

* [Thread 세부 정리](/qt/thread/)
* [Qt Thread - 1](/qt/thread/theorem1/)
* [Qt Thread - 2](/qt/thread/theorem2/) : queue condition에 따라서 어떻게 동작하는지 보여준다.

## Core

* [Qt Core](/qt/core/)

* [QPixmap Rescale]()

> * [참고사이트](https://stackoverflow.com/questions/8211982/qt-resizing-a-qlabel-containing-a-qpixmap-while-keeping-its-aspect-ratio)

```cpp
QPixmap p; // load pixmap
// get label dimensions
int w = label->width();
int h = label->height();

// set a scaled pixmap to a w x h window keeping its aspect ratio 
label->setPixmap(p.scaled(w,h,Qt::KeepAspectRatio));
```

**스마트 포인터**

* [QPointer](/qt/core/QPointer/) : Qt용 포인터
* [QScopedPointer](/qt/core/QScopedPointer/) : 범위 내에서 delete를 하지 않아도 되는 포인터
* [QSharedPointer](/qt/core/QSharedPointer/) : 참조자를 체크하는 shared pointer

## UI

* [Qt UI](/qt/ui/)

* [Qt HWND 얻기]()

```cpp
HWND hwnd = HWND(ui->preview->winId());
```

* [QListWidgetItem 사용](/cpp/qt/qlistwidgetitem)

![](/file/image/qt-gdi-s6-52-image-1.png)

## QML

* [Qt QML](/qt/qml/)

## Etc

* [Qt Etc](/qt/etc/)

* [Qt Creator에서 PlugIn을 못찾는 다면?]() : `QT_PLUGIN_PATH`를 환경변수로 지정해 줘야함. [참고 링크](https://forum.qt.io/topic/82643/application-can-t-start-because-could-not-find-or-load-qt/23)