---
title: "(C++) 연산자와 lvalue"
date: 2020-02-10 00:00:00 -0000
---

```cpp
int operator++(int& a, int)
{
  int temp = a;
  a = a + 1;
  return temp;    // 값 리턴이기에 rvalue
}

int& operator++(int& a)
{
  a = a + 1;
  return a;       // 주소 리턴이기에 lvalue
}

int main()
{
  int n = 0;
  n = 10;
  
  n++ = 20;   // error - operator++(n, int), rvalue
  ++n = 20;   // ok - operator++(n), lvalue
}
```

```cpp
int a = 10, int b = 0;

a + b = 20;   // error - a + b는 값 리턴이기에 rvalue
```

```cpp
int main()
{
  int n = 0;
  int* p = &n;
  
  decltype(n) n1;   // int
  decltype(p) d1;   // int*
  decltype(*p) d2;   // int& -> 표현식이 lvalue가 될 수 있으면 참조형, 없으면 값형
  
  int x[3] = { 1, 2, 3 };
  decltype(x[0]) d3;      // int &
  
  auto a1 = x[0];         // int
  
  decltype(++n) d4;       // int&
  decltype(n++) d5;       // int
}
```