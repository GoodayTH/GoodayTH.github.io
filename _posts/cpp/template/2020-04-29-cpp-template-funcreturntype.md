---
title: "C++ Template : 함수 리턴타입구하기"
permalink: /cpp/template/funcreturntype/                # link 직접 지정
toc: true                       # for Sub-title (On this page)
comments: true                  # for disqus Comments
categories:                     # for categories
date: 2020-04-27 00:00:00 -0000
last_modified_at: 2020-04-27 00:00:00 -0000
sidebar:
  title: "C++"
  nav: cpp
---

```cpp
#include <iostream>
using namespace std;

double hoo(short a, int b) { return 0; }

template<typename T> struct result_type
{
    typedef T type;
};

/*
template<typename T, typename A1, typename A2> 
struct result_type<R(A1, A2)>
{
    typedef R type;
};
*/

template<typename T ... Types> 
struct result_type<R(Types...)>
{
    typedef R type;
};

template<typename T> void foo(const T& t)
{
    // T : double(short, int) 함수 모양
    typename result_type<T>::type ret;
    cout << typeid(ret).name() << endl;
}

int main()
{
    foo(hoo);
}
```

```cpp
int main()
{
    int n = 0;
    foo(n);     // 실수로 int를 보낸다면?
}
```

```cpp
template<typename T> struct result_type
{
    // typedef T type; // 여기를 없애면
    // 에러를 유발하게 된다.
    static_assert(is_function<T>::vlaue, "error");
};
```

```cpp
template<typename T> struct result_type;
// 의도적으로 구현부를 만들지 않아도 된다.
```