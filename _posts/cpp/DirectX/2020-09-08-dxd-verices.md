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

---

## 벡터의 외적과 내적

* [강의](https://www.youtube.com/watch?v=xYDzdQAUF8E&list=PLOKPEzlY4JKSZLgY_jH4danTYinRKIPz1&index=10)

* 내적 : 투영된 길이를 구할때 사용

```cpp
D3DXVECTOR3 v7(3.0f, 0.0f, 0.0f);
D3DXVECTOR3 v8(-3.0f, 0.0f, 0.0f);
float fCos, fDot, fScale;

fDot = D3DXVec3Dot(&v7, &v8);
fScale = D3DXVec3Length(&v7) * D3DXVec3Length(&v8);
fCos = fDot / fScale;
```

* 외적 : 두 벡터가 이루는 평면의 수직 벡터(두 벡터로 이뤄진 한 평면이 앞인지 뒤인지 확인할때 사용)

```cpp
D3DXVECTOR3 v9(3.0f, 0.0f, 0.0f);
D3DXVECTOR3 v10(0.0f, 3.0f, 0.0f);
D3DXVECTOR3 vResult;

D3DXVec3Cross(&vResult, &v1, &v2);
D3DXVec3Normalize(&vResult, &vResult);
```

---

## 정점의 구조

* [강의](https://www.youtube.com/watch?v=cPFikK8_GFs&list=PLOKPEzlY4JKSZLgY_jH4danTYinRKIPz1&index=11)

vertice는 아래와 같이 구성해야한다.

![](/file/image/dxd-vertices-1.png)

흠... 뭔소린지... 예시를 통해서 설명한다.

* 정점을 넣어주는 방향은 시계방향임을 기억하자.

```cpp
struct CUSTOMVERTEX
{
  FLOAT x, y, z, rhw;
  DWORD color;
};

#define D3DFVF_CUSTOMVERTEX (D3DFVF_XYZRHW | D3DFVF_DIFFUSE)

CUSTOMVERTEX vertices[] = {
  {150.0f, 50.0f, 0.5f, 1.0f ,0xffff0000, },
  {250.0f, 250.0f, 0.5f, 1.0f ,0xff00ff00, },
  {50.0f, 250.0f, 0.5f, 1.0f ,0xff00ffff, },
};
```

---

## 정점 버퍼 생성

* [강의](https://www.youtube.com/watch?v=kSTE0_q6p9M&list=PLOKPEzlY4JKSZLgY_jH4danTYinRKIPz1&index=12)

```cpp
LPDIRECT3DVERTEXBUFFER9 pVB;
if(FAILED(pd3dDevice->CreateVertexBuffer(
  3*sizeof(CUSTOMVERTEX), 
  0,
  D3DFVF_CUSTOMVERTEX,
  D3DPOOL_DEFAULT,
  &pVB,
  NULL
)));
```

vertices 버퍼 복사하기

```cpp
VOID* pVertices;
if(FAILED(pVB->Lock(0, sizeof(vertices), (void**)&pVertices, 0)))
  return E_FAIL;

memcpy(pVertices, vertices, sizeof(vertices));
pVB->Unlock();
```

여기까지 하면 정점을 그릴 준비가 된 것이다.

렌더링하기 위한 정점 버퍼의 설정

```cpp
pd3dDevice->SetStreamSource(0, pVB, 0, sizeof(CUSTOMVERTEX));
```

정점 구조를 설정

```cpp
pd3dDevice->SetFVF(D3DFVF_CUSTOMVERTEX);
```

정점출력

```cpp
d3dD3dDevice->DrawPrimitive(D3DPT_POINTLIST, 0, 6); // 점 단위로 출력
d3dD3dDevice->DrawPrimitive(D3DPT_LINELIST, 0, 3); // 선 단위로 출력
d3dD3dDevice->DrawPrimitive(D3DPT_LINESTRIP, 0, 5); // 선 스트림 으로 출력
d3dD3dDevice->DrawPrimitive(D3DPT_TRIANGLELIST, 0, 2); // 삼각형 으로 출력
d3dD3dDevice->DrawPrimitive(D3DPT_TRIANGLESTRIP, 0, 4); // 삼각형 스트림 으로 출력
d3dD3dDevice->DrawPrimitive(D3DPT_TRIANGLEFAN, 0, 4); // 삼각형 팬 으로 출력
```

---