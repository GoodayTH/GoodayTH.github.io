---
title: "Direct3D : Verices"
permalink: dxd/verices/                # link 직접 지정
toc: true                       # for Sub-title (On this page)
comments: true                  # for disqus Comments
categories:                     # for categories
date: 2020-09-08 00:00:00 -0000
last_modified_at: 2020-09-08 00:00:00 -0000
sidebar:
  title: "목차"
  nav: cpp
tag:
  - C++
  - DirectX
category:
  - verices
excerpt: ""
classes: wide
header:
  teaser: /file/image/cpp-page-teaser.gif
---
* [강의](https://www.youtube.com/watch?v=ExFyJAJMuKo&list=PLOKPEzlY4JKSZLgY_jH4danTYinRKIPz1&index=8)

---

## 이론에 대한 설명

* 쉽기에 중요하다 생각되는 내용만 정리
* Direct3D는 왼손좌표계를 사용한다.
* 벡터에 대한 설명

---

## 벡터의 합

* [Get Code](https://github.com/EasyCoding-7/Direct3DExample/tree/master/Dxd-3)

```cpp
#include <d3dx9math.h>

// ...

D3DXVECTOR3 v1(0.f, 3.0f, 0.0f);
D3DXVECTOR3 v2(3.0f, 0.0f, 0.0f);
D3DXVECTOR3 v3;
D3DXVECTOR3 v4(3.0f, 3.0f, 0.0f);
float fLength;

// 벡터의 덧셈
v3 = v1 + v2;               // 3.0f, 3.0f, 0.0f
D3DXVec3Add(&v3, &v1, &v2); // 3.0f, 3.0f, 0.0f

// 벡터의 뺄셈
v3 = v1 - v2;
D3DXVec3Subtract(&v3, &v1, &v2);
```

---

## 벡터의 크기

* [강의](https://www.youtube.com/watch?v=ZFOnOHiwprI&list=PLOKPEzlY4JKSZLgY_jH4danTYinRKIPz1&index=9)

```cpp
// 벡터의 크기 구하기
fLength = D3DXVec3Length(&v4);  // 4.24264050

// 벡터의 크기 변환
float fScale = 2.0f;
D3DXVECTOR3 v5(2.0f, 1.0f, 0.0f);

D3DXVec3Scale(&v5, &v5, fScale); // 4.0f, 2.0f, 0.0f

// 단위 벡터(normalized vector)
D3DXVECTOR3 v6(2.0f, 2.0f, 3.0f);
D3DXVECTOR3 vResult;
float fNormalize;

D3DXVec3Normalize(&vResult, &v6);
fNormalize = D3DXVec3Length(&vResult);
```