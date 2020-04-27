---
title: "C++ Template : parameter pack"
permalink: /cpp/template/parameter/                # link 직접 지정
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
#include <iotraem>
using namespace std;

void goo(int n, double d, const char* s)
{
    cout << "goo : " << n << " " << d << " " << s << endl;
}

template<typename ... Types>
void foo(Types ... args)
{
    // args : Parameter Pack
    cout << sizeof...(args) << endl;    // 3
    cout << sizeof...(Types) << endl;   // 3

    goo(args);  // 파라미터 팩은 인자로 불가능
    goo(args...);   // pack expansion
                    // goo(e1, e1, e3) / goo(1, 3.4, "AAA")
}

int main()
{
    foo();
    foo(1);
    foo(1, 3.4, "AAA"); // Types : int, double, const char* / args : 1, 3.4, "AAA"
}
```