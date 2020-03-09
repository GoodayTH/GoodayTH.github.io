---
title: "(C++) 초기화 코드의 문제"
date: 2020-02-05 00:00:00 -0000
---

## 기존 초기화 코드의 문제

```cpp
int main()
{
  // 1. 초기화 방법이 너무 다양함.
  int n1 = 0;
  int n2(0);
  int ar[3] = { 1, 2, 3 };
  Point p = { 1, 2 };     // 구조체
  complex c(1, 2);        // 클래스
  
  // 2. 클래스 내부의 배열을 초기화 할 방법이 없다.
  class Test
  {
    int x[10];
  };
  
  // 3. 동적메모리할당을 할 경우 초기화 할 방법이 없다.
  int* p = new int[3];
  
  // 4. STL 컨테이너를 초기화하는 편리한 방법이 없다.
  vector<int> v;
  for(int i = 0; i < 10; i++)
    v.push_back(1);
}
```

```cpp
#include <iostream>
using namespace std;

int cnt = 0;

class Test
{
public:
  // int data = 0;   // member initializer
  int data = ++cnt;
  Test() {}
  Test(int n) : data(n) {}
};

int main()
{
  Test t1;      // data는 0으로 초기화
  Test t2(3);
  
  cout << cnt << endl;  // t1, t2 두 번 호출되기에 cnt는 2일까? Nope! 1임
  
  cout << t1.data << endl;
  cout << t2.data << endl;
}
```

```cpp
// 이렇게 하면 2가 나온다.
class Test
{
public:
  int data = ++cnt;
  Test() {}
  Test(int n) // : data(n) {}
  // data가 n으로 초기화 되는 것을 막는경우
};
```