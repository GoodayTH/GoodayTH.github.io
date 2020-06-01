---
title: "C++ Template : parameter"
permalink: cpp/template/parameter/                # link 직접 지정
toc: true                       # for Sub-title (On this page)
comments: true                  # for disqus Comments
categories:                     # for categories
date: 2020-04-25 00:00:00 -0000
last_modified_at: 2020-04-25 00:00:00 -0000
sidebar:
  title: "C++"
  nav: cpp
---

## template parameter #1

```cpp
// type, value(non-type)를 받을 수 있다.
template<typename T, int N> struct Stack
{
    T buff[N];
};

int main()
{
    Stack<int, 10>  s;
}
```

```cpp
// 정수형 상수
template<int N> class Test1 {};

// enum 상수
enum Color {red = 1, green = 2};
template<Color> class Test2 {};

// 포인터
template<int*> class Test3 {};

int x = 0;

// 함수 포인터
template<int(*)(void)> class Test4 {};

int main()
{
    int n = 10;
    Test1<10> t1; // ok
    Test2<n> t2;  // error - 변수안됨

    Test2<red> t3;      // ok
    Test3<&n> t4;       // error - 지역변수 주소안됨., 전역만 가능
    
    Test3<&x> t5;       // ok

    Test5<&main> t6;    // ok
}
```

```cpp
template<auto N> struct Test
{
    Test() { cout << typeid(N).name() << endl; }
};
int x = 0;

int main()
{
    Test<int> t1;       // N : int
    Test<&x> t2;        // N : int*
}
```

---

## template parameter #2

```cpp
template<typename T> class list {};

// template<typename T, list> class stack 라고 생각하자
template<typename T, template<typename> class C> class stack
{
    C c;    // error - list c이기에 에러
    C<T> c; // ok - list<int> c
};

int main()
{
    list s1;        // error
    list<int> s2;   // ok = list<int> 는 타입이란걸 기억하자

    stack<int, list> s3;    // ok
}
```

```cpp
// default parameter
template<typename T, int N = 10> struct Stack
{

};

int main()
{
    Stack<int, 10> s1;
    Stack<int> s2;

    Stack<> s3;     // 모든 인자를 디폴트 값 사용
}
```