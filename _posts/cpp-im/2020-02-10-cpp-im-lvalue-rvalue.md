---
title: "(C++) lvalue와 rvalue"
date: 2020-02-10 00:00:00 -0000
---

```cpp
int f1() { return x; }
int& f2() { return x; }

int main()
{
  int v1 = 10, v2 = 10;
  
  v1 = 20;    // 
  20 = v1;    // error - 등호의 오른쪽에만 놓일 수 있다., 이름이 없기에 단일문장에서만 사용
  v2 = v1;    // lvalue - 등호의 왼쪽과 오른쪽 모두에 놓일 수 있다., 이름을 갖는다
  
  int* p1 = &v1;    // ok
  int* p2 = &10;    // error - rvalue는 주소가 없다.
  
  f1() = 10;    // error, 값리턴은 rvalue
  f2() = 20;    // ok, 주소리턴은 lvalue
}
```

```cpp
const int c = 10;
c = 20;   // c는 r, l value인가?
// c는 이름이 있고, 주소를 갖기에 lvalue라 할 수 있다. (단, 수정 불가능한 lvalue라 명명한다.)
```