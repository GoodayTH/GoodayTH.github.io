---
title: "C++ Template : type traits"
permalink: /cpp/template/traits/                # link 직접 지정
toc: true                       # for Sub-title (On this page)
comments: true                  # for disqus Comments
categories:                     # for categories
date: 2020-04-25 00:00:00 -0000
last_modified_at: 2020-04-25 00:00:00 -0000
sidebar:
  title: "C++"
  nav: cpp
---

## Tratis 정의

```cpp
template<typename T> void printv(T v)
{
    // if( T is Pointer ) // 포인터인지 아닌지를 분석하고 싶다 -> Traits!
        cout << v << " : " << *v << endl;
    cout << v << endl;
}

int main()
{
    int n = 3;
    double d = 3.4;

    printv(n);
}
```

```cpp
template<typename T> struct is_pointer
{
    enum { value=false; }
};

template<typename T> struct is_pointer<T*>      // 포인터타입이 들어오면 여기를 써달라.
{
    enum { value=true; }
};

template<typename T> void foo(T v)
{
    if(is_pointer<T>::value) {    // 포인터를 분석가능
        cout << "pointer" << endl;
    }
    else {
        cout << "not pointer" << endl;
    }
}
```

물론 cpp 표준에 있다.

```cpp
template<typename T> struct is_pointer
{
    // enum { value=false; }
    static constexpr bool value = false;    // 이게 더 좋은 표현
};

template<typename T> struct is_pointer<T*> 
{
    static constexpr bool value = true;
};

template<typename T> void foo(T v)
{
    cout << xis_pointer<int>::value << endl;
    cout << xis_pointer<int*>::value << endl;

    // 아래는 모두 포인터가 아니라고 나오는데 모든 타입에 대해서 template을 만들어야한다.
    cout << xis_pointer<int* const>::value << endl;
    cout << xis_pointer<int* volatile>::value << endl;
    cout << xis_pointer<int* const volatile>::value << endl;
    cout << xis_pointer<int* volatile const>::value << endl;
}
```

---

## is_array

```cpp
#include <iostream>
using namespace std;

template<typename T> struct xis_array
{
    static constexpr bool value = false;
};

template<typename T, size_t N> struct xis_array<T[N]>
{
    static constexpr bool value = true;
    static constexpr size_t size = N;
};

template<typename T> struct xis_array<T>        // 크기를 알수 없는 배열 ex> int[]
{
    static constexpr bool value = true;
};

template<tpyename T> void foo(T& a)
{
    if( xis_array<T>::value )
        cout << "array" << endl;
        cout << "배열 크기 : " << xis_array<T>::size << endl;       // 이런것도 가능! -> extend<T,0>::value C++ 표준에도 있다.
    else
        cout << "not array" << endl;
}

int main()
{
    int x[3] = {1,2,3};
    foo(x);
}
```

