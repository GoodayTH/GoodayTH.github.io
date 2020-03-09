---
title: "(C++) mutable"
date: 2020-01-07 00:00:00 -0000
---

> 상수 멤버 함수 안에서도 값을 변경하고 싶다.

```cpp
#include <iostream>

class Point
{
  int x, y;
  mutable int cnt = 0;
public:
  Point(int a = 0, int b = 0) : x(a), y(b) {}
  
  void print() const
  {
    ++ cnt;
    std::cout << x << ", " << y << std::endl;
  }
};

int main()
{
  Point pt(1, 1);
  pt.print();
  pt.print();
}
```