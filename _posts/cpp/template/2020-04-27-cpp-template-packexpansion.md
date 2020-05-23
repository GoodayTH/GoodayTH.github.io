---
title: "C++ Template : pack expansion"
permalink: cpptemplate/packexpansion/                # link 직접 지정
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

void goo(int a, int b, int c)
{
    cout << a << ", " << b << ", " << c << endl;
}

int hoo(int a) { return -a; }

template<typename ... Types> void foo(Types ... args)
{
    int x[] = {args...};    // pack expansion / {1,2,3}
    int y[] = {(++args)...};    // pack expansion / {2,3,4}
    int z[] = {hoo(args)...};   // hoo(1), hoo(2), hoo(3)

    goo(args...);           // goo(1,2,3)
    goo(hoo(args)...);      // goo(hoo(1), hoo(2), hoo(3));

    for(auto n : x)
        cout << n << endl;
}

int main()
{
    foo(1,2,3);     // Types : int, int, int / args : 1, 2, 3
}
```

```cpp
int print(int a)
{
    cout << a << ", ";
    return 0;
}

template<typename ... Types> void foo(Types ... args)
{
    print(args);        // error
    print(args...);     // error - print(1,2,3)
    print(args)...;  // error - print(1),print(2),print(3)
                        // 전역적 공간에서 pack expansion 불가능

    int x[] = { print(args)... };   // ok - {print(1), print(2), print(3)}

    initializer_list<int> e = { (print(args), 0)...};   // 이런 표현을 더 많이 씀을 알자(이걸쓰자 그냥)
}

int main()
{
    foo(1,2,3);     // args : 1,2,3
}
```

```cpp
#include <iostream>
#include <tuple>
using namespace std;

template<tpyename ... Types> void foo(Types ... args)
{
    // Types : int, double
    pair<Types...> p1;      // pair<int, double>
    tuple<Types...> t1;     // tuple<int, double>

    tuple<pair<Types...>> t2;   // tuple<pair<int, double>> t2
    tuple<pair<Types>...> t3;   // tuple<pair<int>, piar<double>> t3;   // error - pair인데 하나만 인자로 받음
    tuple<pair<int, Types>...> t4;  // tuple<pair<int, int>, pair<int, double>> t4

    pair<tuple<Types...>> p2;       // pair<tuple<int, double>> p2;     // error
    pair<tuple<Types>...> p3;       // pair<tuple<int, tuple<double>> p3;
}

int main()
{
    foo(1, 3.4);
}
```