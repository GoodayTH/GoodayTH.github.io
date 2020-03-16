---
title: "(C++) auto"
date: 2020-02-06 00:00:00 -0000
---

```cpp
// 타입이 추론되는 규칙에 대해 알아보자.
int main()
{
  int n = 10;
  int& r = n;
  
  auto a = r;   // a는 int인가 int&인가
  a = 30;
  
  cout << n << endl;    // 
}
```

```cpp
int main()
{
  int n = 10;
  int& r = n;
  const int c = n;
  const int& cr = c;
  
  auto a1 = n;      // int
  auto a2 = r;      // int (int&가 아님을 주의하자, auto는 값 복사이기에 r의 값을 확인)
  auto a3 = c;      // int (const속성은 무시된다.)
  auto a4 = cr;     // int
  
  auto& a5 = n;     // auto : int, a5 : int&
  auto& a6 = r;     // auto : int, a6 : int&
  auto& a7 = c;     // auto : const int, a7 : const int&
  auto& a8 = cr;    // auto : const int, a8 : const int&
  
  const char* s1 = "hello";   // s1 자체는 const아님
                              // s1을 따라가면 const
  auto a9 = s1;     // const char*
  
  const char* const s2 = "hello";
  auto a10 = s1;    // const char*
}
```
