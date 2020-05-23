---
title: "C++ Template : typename"
permalink: /cpp/template/typename/                # link 직접 지정
toc: true                       # for Sub-title (On this page)
comments: true                  # for disqus Comments
categories:                     # for categories
date: 2020-04-25 00:00:00 -0000
last_modified_at: 2020-04-25 00:00:00 -0000
sidebar:
  title: "C++"
  nav: cpp
---

## typename

```cpp
class Test
{
public:
    enum { value = 1 };
    static int value2;

    typedef int INT;
    using SHORT = short;        // C++11

    class innerClass {};
};
int Test::value2 = 1;

int main()
{
    // 값
    int n1 = Test::value1;
    int n2 = Test::value2;

    // 타입
    Test::INT a;
    Test::SHORT b;
    Test::innerClass c;
}
```

```cpp
int p = 0;

class Test
{
public:
    // ...
};

template<typename T>
int foo(T t) // T : Test
{
    T::DWORD * p;   // 값 : 5 * p : 연산
                    // 타입 : 지역변수 선언
    // 컴파일러는 어떻게 판단할까?

    T::DWORD * p;               // 값으로 판단 error!
    typename T::DWORD * p;      // 타입으로 판단
    return 0;
}

int main()
{
    Test t;
    foo(t);
}
```

---

## value_type #1

```cpp
#include <iostream>
#include <vector>
#include <list>
using namespace std;

/*
void print_first_element(vector<int>& v)
{
    int n = v.front();
    cout << n << endl;
}
*/

template<typename T>
void print_first_element(vector<T>& v)
{
    T n = v.front();
    cout << n << endl;
}

int main()
{
    vector<int> v = { 1, 2, 3 };
    print_first_element(v);

    list<int> l = { 1, 2, 3 };
    print_first_element(l);     // error
}
```

```cpp
template<typename T>
void print_first_element(T& v)
{
    // ??? n = v.front();
    T::value_type n = v.front();
    // auto n = v.front();      // 물론 이런 선언이 가능하다
    cout << n << endl;
}
```

---

## value_type #2

```cpp
#include <list>
using namespace std;

template<typename T> class Vector
{
    T* buff;
    int size;
public:
    Vector<int sz, T value> {}
};

int main()
{
    // Vector<int> v(10, 3);
    Vector v(10, 3);            // 이렇게 선언해도 가능
    list<int> s = {1,2,3};

    // 아래는 가능한가?
    Vector v2(s);
}
```

```cpp
template<typename T> class Vector
{
    T* buff;
    int size;
public:
    Vector<int sz, T value> {}

    template<typename C> Vector<C c> {}
};
template<typename C> 
Vector<C c>->Vector<typename C::value_type>;
```

---

## template

```cpp
class Test
{
public:
    template<typename T> static void f() {}
    template<typename T> class Complex {}
};

template<typename T> void foo(T a)
{
    Test::f<int>();     // ok
    T::f<int>();        // error
    T::template f<int>();       // ok - T가 template임을 알려줘야한다.

    Test::Complex<int> c1;      // ok
    T::Complex<int> c2;         // error
    typename T::template Complex<int> c3;   // ok
}

int main()
{
    Test t;
    foo(t);
}
```