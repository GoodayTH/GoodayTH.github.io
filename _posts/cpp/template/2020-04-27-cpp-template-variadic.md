---
title: "C++ Template : Variadic Template"
permalink: /cpp/template/variadic/                # link 직접 지정
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
template<typename T> class tuple
{

};

int main()
{
    tuple<int> t1;
    tuple<int, char> t2;    // error
}
```

가변인자 템플릿을 만들어보자. -> C++11부터 지원됨을 기억하자.

```cpp
template<typename ... Types> class tuple
{

};

int main()
{
    tuple t0;
    tuple<int> t1;
    tuple<int, char> t2;    // ok
}
```

가변인자 템플릿 함수도 가능.

```cpp
template<typename ... Types> void foo(Types ... arg)
{
}
```


