---
title: "C++ Template : get function result & argument"
permalink: cpptemplate/get_result/                # link 직접 지정
toc: true                       # for Sub-title (On this page)
comments: true                  # for disqus Comments
categories:                     # for categories
date: 2020-04-26 00:00:00 -0000
last_modified_at: 2020-04-26 00:00:00 -0000
sidebar:
  title: "C++"
  nav: cpp
---

```cpp
double hoo(short a, int b) { return 0; }

template<typename T> strcut result_type
{
    typedef T type;
};

template<typename R, typename A1, typename A2> strcut result_type<R<A1, A2>>
{
    typedef R type;
};

template<typename T> void foo(T& b)
{
    // T : double(short, int)
    typename result_type<T>::type ret;
    cout <<< typeid(ret).name() << endl;
}

int main()
{
    foo(hoo);
}
```

```cpp
double hoo(short a, int b) { return 0; }

template<typename T, size_t N> struct argument_type
{
    typedef T type;
};

/* // 이렇게 쓰면 몇번재 인자를 리턴해달라는지 알수 없음.
template<typename R, typename A1, typename A2, size_t N> struct argument_type<R(A1, A2), N>
{
    typedef T type;
};
*/

template<typename R, typename A1, typename A2> struct argument_type<R(A1, A2), 0>
{
    typedef A1 type;
};

template<typename R, typename A1, typename A2> struct argument_type<R(A1, A2), 1>
{
    typedef A2 type;
};

template<typename T> void foo(T& t)
{
    typename argument_type<T, 0>::type ret;
    cout << typeid(ret).name() << endl;
}

int main()
{
    foo(hoo);
}
```