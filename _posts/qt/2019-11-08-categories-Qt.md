---
title: "Qt"
permalink: qt/                # link 직접 지정
toc: true                       # for Sub-title (On this page)
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

## UI

* [Qt UI](/qt/ui/)

* [Qt HWND 얻기]()

```cpp
HWND hwnd = HWND(ui->preview->winId());
```

* [QListWidgetItem 사용](/cpp/qt/qlistwidgetitem)

![](/file/image/qt-gdi-s6-52-image-1.png)

## Thread

* [Qt Thread](/qt/thread/)

## QML

* [Qt QML](/qt/qml/)

## Etc

* [Qt Etc](/qt/etc/)
