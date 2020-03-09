---
title: "(C++) suffix 후위리턴"
date: 2020-01-07 00:00:00 -0000
---

```cpp

// int suqare(int a)
auto square(int a) -> int   // 후위 반환 타입
{
  return a * a;
}

int main()
{
  square(3);
}
```

---

> 어디다 쓰나?

```cpp
/*
int add(int a, int b)
{
  return a + b;
}
*/
template<typename T>
T add(T a, T b)
{
  return a + b;
}

int main()
{
  add(1, 2);    // ok
  add(1, 1.2);  // compile error
}
```

```cpp
template<typename T1, typaname T2>
?? add(T1 a, T2 b) // 리턴형은 뭘로 선언해야하나??
{
  return a + b;
}
```

```cpp
template<typename T1, typaname T2>
auto add(T1 a, T2 b) -> decltype(a+b)   // C++11
auto add(T1 a, T2 b)  // C++14
{
  return a + b;
}
```