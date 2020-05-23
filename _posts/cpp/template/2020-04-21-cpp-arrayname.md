---
title: "C++ Template : 배열의 이름은 주소일까?"
permalink: /cpp/template/arrayname/                # link 직접 지정
toc: true                       # for Sub-title (On this page)
comments: true                  # for disqus Comments
categories:                     # for categories
date: 2020-04-21 00:00:00 -0000
last_modified_at: 2020-04-21 00:00:00 -0000
sidebar:
  title: "C++"
  nav: cpp
---

```cpp
int main
{
    int x[3] = {1,2,3};
    int* p = x;         // 배열은 이름은 주소일까?
}
```

```cpp
int main()
{
    int n;
    int* p1 = &n;

    double d;

    int x[3] = {1,2,3}; // 변수이름 : x, 타입 : int[3]

    // 배열 x의 주소
    int (*p3)[3] = &x;  // 배열의 주소
    int* p4 = x;        // 배열의 주소가 아님!
}
```

```cpp
int main()
{
    int n1 = 10;
    int n2 = n1;

    int x1[3] = {1,2,3};    // x1의 타입 : int[3]
    int x2[3] = x1;         // error -> 배열은 자신과 동일한 타입으로 복사가 안된다.

    int* p1 = x1;                // 배열의 이름은 첫번째 요소 주소로 암시적 형변환
}
```

* [Run This Code](https://ideone.com/F5zlpH)

```cpp
#include <stdio.h>

int main()
{
    int x[3] = {1,2,3};

    int(*p1)[3] = &x;

    int* p2 = x;

    printf("%p\n", p1);
    printf("%p\n", p2);
}
```

![](/file/image/cpp-array-name.png)

똑같은디?? 무슨차인가??

```cpp
printf("%p, %p\n",p1, p1+1);        // 12
printf("%p, %p\n",p2, p2+1);        // 4
```

![](/file/image/cpp-array-name2.png)

```cpp
// p1 : 배열의 주소, *p1 : 배열
(*p1)[0] = 10;

// p2 : 요소의 주소, (int*)
*p2 = 10;

// 위와같이 요소를 넣는 방법이 다르다.
```