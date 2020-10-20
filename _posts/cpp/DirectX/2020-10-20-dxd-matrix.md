---
title: "Direct3D : Matrix"
permalink: dxd/matrix/                # link 직접 지정
toc: true                       # for Sub-title (On this page)
comments: true                  # for disqus Comments
categories:                     # for categories
date: 2020-10-20 00:00:00 -0000
last_modified_at: 2020-10-20 00:00:00 -0000
sidebar:
  title: "목차"
  nav: cpp
tag:
  - C++
  - DirectX
category:
  - matrix
excerpt: ""
classes: wide
header:
  teaser: /file/image/cpp-page-teaser.gif
---

* [강의](https://www.youtube.com/watch?v=RgfjJ3q7CSg&list=PLOKPEzlY4JKSZLgY_jH4danTYinRKIPz1&index=14)
* [Get Code]()

---

## 행렬(matrix) 사용해보기

```cpp
D3DXMATRIX matIdentity, matMatrix, matResult;
D3DXMatrixIdentity(&matIdentity);       // 단위행렬 만들기

for(int i = 0; i < 4; i++)
{
    for(int j = 0; j < 4; j++)
    {
        // matrix에 값 대입
        matMatrix(i, j) = float(i * 4 + j + 1);
    }
}

matResult = matMatrix * matIdentity;    // 단위행렬 곱하기
// D3DXMatrixMultiply(&matReult, &matMatrix, &matIdentity); // 곱셈과 동일

for(int i = 0; i < 4; i++)
{
    for(int j = 0; j < 4; j++)
    {
        printf("%7.1f", matReult.m[i][j]);
    }
    printf("\n");
}
```

---

## 전치 행렬

* [강의](https://www.youtube.com/watch?v=TEP7djs_pV4&list=PLOKPEzlY4JKSZLgY_jH4danTYinRKIPz1&index=15)

```cpp
D3DXMATRIX matMatrix, matResult;

for(int i = 0; i < 4; i++)
{
    for(int j = 0; j < 4; j++)
    {
        // matrix에 값 대입
        matMatrix(i, j) = float(i * 4 + j + 1);
    }
}

for(int i = 0; i < 4; i++)
{
    for(int j = 0; j < 4; j++)
    {
        printf("%7.1f", matMatrix.m[i][j]);
    }
    printf("\n");
}

D3DXMatrixTranspose(&matResult, &matMatrix);
for(int i = 0; i < 4; i++)
{
    for(int j = 0; j < 4; j++)
    {
        printf("%7.1f", matResult.m[i][j]);
    }
    printf("\n");
}
```

## 역행렬

```cpp
D3DXMATRIX matMatrix, matResult;
D3DXMatrixRotationX(&matMatrix, 0.3f);

// 회전 행렬
for(int i = 0; i < 4; i++)
{
    for(int j = 0; j < 4; j++)
    {
        printf("%7.1f", matMatrix.m[i][j]);
    }
    printf("\n");
}

// 역행렬
D3DXMatrixInverse(&matResult, NULL, &matMatrix);

for(int i = 0; i < 4; i++)
{
    for(int j = 0; j < 4; j++)
    {
        printf("%7.1f", matResult.m[i][j]);
    }
    printf("\n");
}
```