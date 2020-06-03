---
title: "Unity"
permalink: unity/                # link 직접 지정
toc: true                       # for Sub-title (On this page)
comments: true                  # for disqus Comments
categories:                     # for categories
date: 2020-06-02 00:00:00 -0000
last_modified_at: 2020-06-02 00:00:00 -0000
header:
  teaser: /file/image/unity-page-teaser.gif
sidebar:
  title: "unity" 
  nav: unity
tag:
  - Unity
category:
  - category
excerpt: "Unity 및 C#과 관련된 지식을 정리한 페이지 입니다."
header:
  overlay_image: /file/image/main-page.jpg
  overlay_filter: 0.1 # rgba(255, 0, 0, 0.5)
  caption: "Photo credit: [**EBS**](https://ebs.co.kr)"
  actions:
    - label: "Unity HomePage"
      url: "https://unity3d.com//"
---

## C#

기본적 문법

```csharp
// 주석

/* 
* 주석
*/

// 콘솔 로그 출력
int num = 0;
Debug.Log("로그" + num);

// 함수선언
float GetRadius(float size)
{
  // ...
}

// 배열 선언
int[] scores = new int[10];

// 상속
public class Animal
{
  public string name;
  string sound;
  float weight;
}

Animal jack = new Animal();
```