---
title: "C++ Template : Instantiation"
permalink: cpp/template/Instantiation/                # link 직접 지정
toc: true                       # for Sub-title (On this page)
comments: true                  # for disqus Comments
categories:                     # for categories
date: 2020-04-21 00:00:00 -0000
last_modified_at: 2020-04-21 00:00:00 -0000
sidebar:
  title: "C++"
  nav: cpp
---

```cpp
template<typename T>
T square(T a)
{
    return a * a;
}
// 이렇게 template만 만들면 실제로 메모리에 square라는 함수를 만들어지진 않았다.

int main()
{
    square<int>(3);     // 선언을 하면 메모리에 올라가고 이를 Template Instantiation이라 한다.
}
```

* Template instantiation
    * 컴파일러가 함수(클래스) 템플릿으로 부터 실제 함수(클래스)를 만들어 내는 과정
    * 명시적/ 암시적 인스턴스화로 나눌 수 있다.

```cpp
int add(int a, int b)
{
    return a + b;
}

template<typename T>
T square(T a)
{
    return a * a;
}

int main()
{
    
}
```

어셈블리 코드에서 보면 main, add를 확인할 수 있지만 square은 없다.

```cpp
int main()
{   
    square<int>(3);
    square<double>(3.3);
}
```

이제 어셈블리 코드에서 square int, double형이 만들어졌음을 알 수 있다.

---

* 명시적 인스턴스화(explicit instantiation)
    * 템플릿을 사용해서 특정 타입의 함수(클래스)를 생성해 달라고 명시적으로 지시
* 암시적 인스턴스화(implicit instantiation)
    * 명시적 인스턴스화를 하지 않고 템플릿을 사용하는 경우, 암시적으로 인스턴스화가 발생

## 명시적 인스턴스화

```cpp
template<typename T> class Test
{
public:
    void foo() {}
    void goo() {}
};

template<typename T> T square(T a)
{
    return a * a;
}

template int square<int>(int);      // 명시적으로 선언됨. - 메모리에 올라간다.
template int square(int);           // 이렇게 쓰기도 한다.

template class Test<int>;           // 클래스도 명시적 선언이 가능하다.
template class Test<int>::foo();    // 클래스 내의 특정함수만 명시적 선언이 가능하다.

int main()
{

}
```

## 암시적 인스턴스화

```cpp
template<typename T> class Test
{
public:
    void foo() {}
    void goo() {}
};

template<typename T> T square(T a)
{
    return a * a;
}

int main()
{
    int n = square(3);           // 그냥 쓰면 그게 암시적 인스턴스화이다.
    int n2 = square<int>(3);        

    Test<int> t1;               // 클래스 역시 암시적 인스턴스화가 가능하다.
    t1.foo();                   // 사용된 함수만 인스턴스화가 된다는 점을 기억하자.
}
```

---

## type deduction

```cpp
template<typename T> T square(T a)
{
    return a * a;
}

int main()
{
    square<int>(3);     // ok
    square(3);          // ok - 컴파일러가 인자를 보고 추론 -> type deduction
}
```

클래스도 type deduction이 가능한가??

```cpp
template<typename T> class Vector
{
    T* buff;
public:
    Vector() {}
    Vector(int sz, T initValue) {}
};

int main()
{
    Vector<int> v1(10, 3);          // ok
    Vector v2(10, 3);               // C++17 - ok - 컴파일러가 생성자를 보고 추론

    Vector v3;                      // error - 컴파일러입장에서 T를 추론할 수 없다.
}
```

```cpp
// user define decution guide
Vector()->Vector<int>;              // 디폴트 생성자를 생성시 int로 만들어 달라

int main()
{
    Vector v3;                     // ok - 물론 추천하는 방식은 아니다.
}
```

```cpp
template<typename T> class Vector
{
    T* buff;
public:
    Vector() {}
    Vector(int sz, T initValue) {}

    template<typename C> Vector(C& c) {}
};

// user define decution guide
Vector()->Vector<int>;
template<typename C> Vector(C& c)->Vector<typenae C::value_type>;

int main()
{
    list s = {1,2,3};       // only C++ 17 ~
    Vector v4(s);       
}
```