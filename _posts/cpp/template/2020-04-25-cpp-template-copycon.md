---
title: "C++ Template : copy constructor"
permalink: /cpp/template/copycon/                # link 직접 지정
toc: true                       # for Sub-title (On this page)
comments: true                  # for disqus Comments
categories:                     # for categories
date: 2020-04-25 00:00:00 -0000
last_modified_at: 2020-04-25 00:00:00 -0000
sidebar:
  title: "C++"
  nav: cpp
---

```cpp
template<typename T> class Complex
{
    T re, im;
public:
    Complex(T r = {}, T i = {}) : re(r), im(i) {}
};

int main()
{
    Complex<int> c1(1, 1);      // ok
    Complex<int> c2 = c1;       // ok - 기본 복사생성자가 만들어진다.

    Complex<double> c3 = c1;    // error - 자료형이 달라서 기본 복사생성자로 불가능!
}
```

복사생정자를 만들어보자.

```cpp
template<typename T> class Complex
{
    T re, im;
public:
    Complex(T r = {}, T i = {}) : re(r), im(i) {}
    Complex(const Complex<T>& c) {}     // 일반적 복사생성자
    Complex(const Complex<int>& c) {}   // 이렇게 선언하면 Complex<int>에 대한 복사생성만 하겠다는 말.

    template<typenmae U>
    Complex(const Complex<U>& c) {}
};

int main()
{
    Complex<double> c3 = c1;        // okay
}
```

```cpp
template<typename T> class Complex
{
    T re, im;
public:
    Complex(T r = {}, T i = {}) : re(r), im(i) {}
    template<typenmae U>
    Complex(const Complex<U>& c) {}     // 일반화된 복사 생성자

    template<typename> friend class Complex;
};

template<typename T> template<typenmae U>
Complex<T>::Complex(const Complex<U>& c) : re(c.re), im(c.im)
{
}
```

```cpp
#include <memory>
using namespace std;

class Animal {};
class Dog : public Animal {};

int main()
{
    // 이런 동작이 모두 template으로 동작한다.
    shared_ptr<Dog> p1(new Dog);
    shared_ptr<Animal> p2 = p1;     // ok

    p2 = p1;

    if(p2 == p1){}  // ok
}
```