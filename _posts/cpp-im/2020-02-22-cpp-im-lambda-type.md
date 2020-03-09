---
title: "(C++) lambda expression & type"
date: 2020-02-22 00:00:00 -0000
---

```cpp
#include <iostream>
#include <algorithm>
using namespace std;

int main()
{
    // lambda expression 활용 1. 함수 인자로 사용
    sort(x, x+10, [](int a, int b){ return a < b; });

    // 활용 2. auto변수에 담아서 함수처럼 사용.
    auto f = [](int a, int b){ return a + b; };
    cout << f(1,2) << endl;
}
```

```cpp
int main()
{
    auto f1 = [](int a, int b) { return a + b; };
    cout << type(f1).name() << endl; // 컴파일러마다 type이 다르다.
    auto f2 = [](int a, int b) { return a + b; };
    cout << type(f2).name() << endl; // 호출될 때마다 type이 달라진다.

    f2 = [](int a, int b) { return a + b; };    // 이런 호출이 불가능하다.
}
```