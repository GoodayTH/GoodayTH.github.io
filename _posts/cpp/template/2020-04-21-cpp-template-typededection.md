---
title: "C++ Template : type deduction"
permalink: cpp/template/typededuction/                # link 직접 지정
toc: true                       # for Sub-title (On this page)
comments: true                  # for disqus Comments
categories:                     # for categories
date: 2020-04-21 00:00:00 -0000
last_modified_at: 2020-04-21 00:00:00 -0000
sidebar:
  title: "C++"
  nav: cpp
---

## boost::type_index

```cpp
#include <iostream>
#include <boost\type_index.hpp>
using namespace std;
using namespace boost::typeindex;

template<typename T> void foo(const T a)
{
    cout << type_id_with_cvr<T>().pretty_name() << endl;
    cout << type_id_with_cvr<decltype(a)>().pretty_name() << endl;      // const까지 조사가 가능
}

int main()
{
    foo<int>(3);

    foo(3);         // T : int, a : const int
    foo(3.3);       // T : double, a : const double
}
```

---

## template type deduction

```cpp
template<typename T> void foo(T a)
{
    ++a;
}

int main()
{
    int n = 0;
    int& r = n;
    const int c = n;

    foo(n);     // T : int
    foo(c);     // T : const int ? int -> int
    foo(r);     // T : int& ? int -> int
}
```

* Template Argument Type Deduction
    * 컴파일러가 함수 인자를 보고 템플릿의 타입을 결정
    * 함수 인자의 타입과 완전히 동일한 타입으로 결정이 되지않는다 -> 큰 혼란을 막기위함

```cpp
template<typename T> void foo(T a)      // foo(T& a)이 아니기에 무조건 값으로 받음 -> const, volatile, reference 속성을 제거한다.
{
    cout << type_id_with_cvr<T>().pretty_name() << endl;
}

int main()
{
    int n = 0;
    int& r = n;
    const int c = n;
    const int& cr = c;

    foo(n);     // T : int
    foo(c);     // T : int
    foo(r);     // T : int
    foo(cr);    // T : int

    const char* s1 = "hello";       // s1을 따라가면 const
    foo(s1);        // char const *

    const char* const s2 = "hello";
    foo(s2);        // char const*
}
```

```cpp
template<typename T> void foo(T& a)     // 참조일때 확인하자
{
    cout << type_id_with_cvr<T>().pretty_name() << endl;
    cout << type_id_with_cvr<decltype(a)>().pretty_name() << endl;
}

template<typename T> void goo(const T& a)     // 참조일때 확인하자
{
    cout << type_id_with_cvr<T>().pretty_name() << endl;
    cout << type_id_with_cvr<decltype(a)>().pretty_name() << endl;
}

int main()
{
    int n = 0;
    int& r = n;
    const int c = n;
    const int& cr = c;

    foo(n);     // T : int, a : int&
    foo(c);     // T : int, a : int& -> const를 int&로 받는다고??
                // T : const int, a : const int& 이다.
    foo(r);     // T : int, a : int& -> reference속성은 제거가 된다. 단 volatile, const속성은 유지된다.
    foo(cr);    // T : const int, a : const int&

    goo(n);     // T : int, a : const int&
    goo(c);     // T : int, a : const int&
    goo(r);     // T : int, a : const int&
    goo(cr);    // T : int, a : const int&
}
```

---

## array name

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

---

## argument decay

```cpp
template<typename T>
void foo(T a)
{
    cout << type_id_wid_cvr<T>().pretty_name() << endl;
    cout << type_id_wid_cvr<decltpye(a)>().pretty_name() << endl;
}

template<typename T>
void goo(T& a)
{
    cout << type_id_wid_cvr<T>().pretty_name() << endl;
    cout << type_id_wid_cvr<decltpye(a)>().pretty_name() << endl;
}

int main()
{
    int x[3] = {1,2,3};

    int y[3] = x;       // error
    int* p = x;         // ok
    int(&r)[3] = x;     // ok

    foo(x);             // T : int[3] - error / T : int*
    goo(x);             // T : int(&a)[3] 
}
```

```cpp
template<typename T> void foo(T a, T b)
{

}

template<typename T> void goo(T& a, T& b)
{
    
}

int main()
{
    foo("orange", "apple");     // ok
    goo("orange", "apple");     // error - "orange" const char[6], "apple" const char[5] 다른 T가 되기에 에러가 된다.

    goo("orange", "aapple");    // ok
}

```