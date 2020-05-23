---
title: "C++ Template : Instantiation2"
permalink: cpp/template/Instantiation2/                # link 직접 지정
toc: true                       # for Sub-title (On this page)
comments: true                  # for disqus Comments
categories:                     # for categories
date: 2020-04-21 00:00:00 -0000
last_modified_at: 2020-04-21 00:00:00 -0000
sidebar:
  title: "C++"
  nav: cpp
---

## technic

```cpp
template<typename T> void foo(T a) {}

template<typenmae T, typename U> struct pair
{
    T first;
    U second;
    pair(const T& a, const U& b) : first(a), second(b) {}
};

// 함수 템플릿
template<typename T, typename U>
pair<T, U> make_pair(const T& a, const U& b)
{
    // make_pair에서 타입을 추론해준다.
    return pair<T, U>(a, b);
}

int main()
{
    pair<int, double> p(1, 3.4);
    foo(p);

    foo(pair<int, double>(1, 3.4));     // 가장 기본적인 방식

    foo(make_pair(1, 3.4));             // C++17 이전 방식
    // foo(make_tuple(1, 3.4, 1));      // make_tuple도 있음을 기억!

    foo(pair(1, 3.4));                  // C++17 이후 방식
}
```

## identity

타입을 명확화 하고싶을 때 사용

```cpp
template<typename T> struct identity
{
    typedef T type;
};

template<typneame T> void foo(T a) {}
template<typneame T> void goo(typename identity<T>::type a) {}

int main()
{
    identity<int>::type n;      // identity<int>::type = int -> 이게뭐지??

    foo(3);             // ok
    foo<int>(3);        // ok

    goo(3);             // error - identity를 확인할 수 없다.
    goo<int>(3);        // ok
}
```

---

```cpp
#include <iostream>
using namespace std;

template<typename T> T square(T a)
{
    return a * a;
}

int main()
{
    printf("%p\n", &square);        // 함수의 주소가 나올까?? -> template이기에 errro!
    printf("%p\n", &square<int>);   // ok - 인스턴스화 되며 메모리에 올라간다
    printf("%p\n", static_cast<int(*)(int)>(&square));      // ok 역시 인스턴스화 됨.

    auto p = &square<int>;      // ok
}
```

---

```cpp
// Lib.h
template<typename T> T square(T a)
```

```cpp
// Lib.cpp
template<typename T> T square(T a)
{
    return a * a;
}
```

template은 이렇게 쓰면 에러난다. 선언(*.h)에 다 몰아 넣어야한다.

```cpp
// Lib.h
template<typename T> T square(T a)
{
    return a * a;
}
```

템플릿은 헤더파일로 제공해야한다.