---
title: "C++ Template : integral_constant"
permalink: /cpp/template/intcons/                # link 직접 지정
toc: true                       # for Sub-title (On this page)
comments: true                  # for disqus Comments
categories:                     # for categories
date: 2020-04-26 00:00:00 -0000
last_modified_at: 2020-04-26 00:00:00 -0000
sidebar:
  title: "C++"
  nav: cpp
---

## int2type #1

```cpp
void foo(int n) {}
void foo(double d) {}

int main()
{
    foo(3);     // int
    foo(3.4);   // double

    foo(0);     // int말고 다른 타입을 부르고 싶다 -> int2type
    foo(1);     
}
```

```cpp
template<int N> struct int2type
{
    enum { value = N };
};

void foo(int n) {}

int main()
{
    int2type<0> t0;
    int2type<1> t1;     // t0, t1은 다른 타입이다

    foo(t0);
    foo(t1);        // foo(t0), foo(t1)은 다른 함수 호출
}
```

```cpp
#include <iostream>
using namespace std;

template<typename T> void printv(T v)
{
    // if( T is Pointer )
    if( xis_pointer<T>::value )
        cout << v << " : " << *v << endl;
    else
        cout << v << endl;
}

int main()
{
    int n = 3;
    printv(n);      // error - if문은 실행시간 조건문이라 if문 내부를 모두 컴파일해버리며 문제가 발생한다.
    printv(&n);
}
```

```cpp
#include <iostream>
using namespace std;

template<typename T> void printv(T v)
{
    // if( T is Pointer )
    if constexpr ( xis_pointer<T>::value )  // C++17 이후 문법임
        cout << v << " : " << *v << endl;
    else
        cout << v << endl;
}

int main()
{
    int n = 3;
    printv(n);      // okay
    printv(&n);
}
```

```cpp
#include <iostream>
using namespace std;

template<typename T> void printv_imp(T v, int2type<1>)
{
    cout << v << " : " << *v << endl;
}

template<typename T> void printv_imp(T v, int2type<0>)
{
    cout << v << endl;
}

template<typename T> void printv(T v)
{
    printv_imp(v, int2type<xis_pointer<T>::value>());
}

int main()
{
    int n = 3;
    printv(n);      // okay
    printv(&n);
}
```

---

## integral_constant

```cpp
#include <iostream>
using namespace std;

template<typename T, T N> struct integral_constant
{
    static constexpr T value = N;
};

integral_constant<int, 0> t0;
integral_constant<int, 1> t1;
integral_constant<short, 0> t2;

// 아래는 C++표준에 선언되어 있음.
typedef integral_constant<bool, true> true_type;
typedef integral_constant<bool, false> false_tpye;

// is_pointer를 만들때
template<typename T> struct is_pointer : false_type
{
    // value = false; // false_type에 포함되어 있다.
};

template<typename T> struct is_pointer : true_tpye {};

int main()
{

}
```

```cpp
#include <iostream>
#include <type_traits>
using namespace std;

template<typename T>
void printv_imp(T, v, true_type)
{
    // ...
}

template<typename T>
void printv_imp(T, v, false_type)
{
    // ...
}

template<typename T> void printv(T v)
{
    printv_imp(v, is_pointer<T>());
}

int main()
{
    int n = 3;
    printv(n);
    printv(&n);
}
```

---

## type query using traits

```cpp
#include <iostream>
#include <type_traits>
using namespace std;

template<typenmae T> void foo_imp(T v, true_type)
{
    // *v = 10;     // ok
}

template<typenmae T> void foo_imp(T v, false_type)
{
    
}

template<typename T> void foo(int v)
{
    // T가 포인터인지 확인
    // if( is_pointer<T>::value ) // *v = 10 역 참조가 안되기에 문제가 있다.

    foo_imp(v, is_pointer<T>());
}

int main()
{
    int n = 0;
    foo(n);
    foo(&n);
}
```