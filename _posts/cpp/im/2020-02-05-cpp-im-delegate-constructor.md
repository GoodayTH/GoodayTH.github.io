---
title: "(C++) delegate constructor"
date: 2020-02-05 00:00:00 -0000
---

```cpp
#include <iostream>
using namespace std;

struct Point
{
  int x, y;
  Point() : x(0), y(0) {}
  Point(int a, int b) : x(a), y(b) {}
  // 생성자 안에서 하는 일이 많다면?? 생성자 모두에 다 구현해줘야할까?
};

int main()
{
  Point p;
  
  cout << p.x << endl;
  cout << p.y << endl;
}
```

> 그래서 그런데 ...

```cpp
struct Point
{
  int x, y;
  Point() : {
    Point(0, 0);    // 이런선언이 가능할까? -> Nope 임시객체를 만드는 선언이지 생성자를 재 호출하는 선언이 아니다.
  }
  Point(int a, int b) : x(a), y(b) {}
};
```

> 위임생성자의 탄생

```cpp
struct Point
{
  int x, y;
  Point() : Point(0,0) {}     // delegate constructor(위임 생성자)
  Point(int a, int b) : x(a), y(b) {}
};
```