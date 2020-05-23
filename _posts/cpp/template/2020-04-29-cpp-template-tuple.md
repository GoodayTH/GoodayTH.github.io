---
title: "C++ Template : tuple"
permalink: cpp/template/tuple/                # link 직접 지정
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
#include <tuple>
using namespace std;

int main()
{
    tuple<> t0;
    tuple<int> t1(1);
    tuple<int, double, int, char> t4(1, 3.4, 2, 'a');

    get<2>(t4) = 10;

    cout << get<2>(t4) << endl;     // 10
}
```

---

## tuple 만들기

```cpp
#include <iostream>
using namespace std;

template<typename ... Types> struct xtuple
{
    static constexpr int N = 0;
};

// 부분 특수화
template<typename T, typename ... Types> 
struct xtuple<T, Types...>
{
    T value;

    xtuple() = default;
    xtuple(const T& v) : value(v) {}

    static constexpr int N = 1;
};

int main()
{
    xtuple<> t0;
    xtuple<int> t1(1);
    xtuple<int, double, int, char> t4(1, 3.4, 2, 'a');
}
```

```cpp
template<typename T, typename ... Types> 
struct xtuple<T, Types...> : public xtuple<Types...>
{
    T value;

    xtuple() = default;
    xtuple(const T& v, const Types... args) 
                : value(v), xtuple<Types...>(args...) {}

    static constexpr int N = xtuple<Types...>::N+1;
};
```