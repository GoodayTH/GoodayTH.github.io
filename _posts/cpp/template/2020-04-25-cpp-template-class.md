---
title: "C++ Template : class template"
permalink: cpp/template/class/                # link 직접 지정
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
    void foo(Complex c)         // ok - (Complex<T> c) 라고 해석됨.
    {
        Complex c_;             // ok
    }
};

void foo(Complex c)         // error
{
}

int main()
{
    Complex c1;             // error
    Complex<int> c2;        // ok
}
```

```cpp
template<typename T> class Complex
{
    T re, im;
public:
    Complex(T a = {}, T b = {}) : re(a), im(b) {}
    T getReal() const; {}       // 아래와 같이 선언해야함
    static int cnt;

    // 클래스 템플릿의 멤버함수 템플릿
    template<typename U> T func(const U& c);
};

template<typename T> 
T Complex<T>::getReal() const
{
    return re;
}

template<typename T> 
int Complex<T>::cnt = 0;

template<typename T> template<typename U>
T Complex<T>::func(const U& c)
{

}

int main()
{

}
```