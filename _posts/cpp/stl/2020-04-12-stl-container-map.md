---
title: "STL : map"
permalink: /cpp/stl/associative/map/                # link 직접 지정
toc: true                       # for Sub-title (On this page)
comments: true                  # for disqus Comments
categories:                     # for categories
date: 2020-04-12 00:00:00 -0000
last_modified_at: 2020-04-12 00:00:00 -0000
sidebar:
  title: "C++"
  nav: cpp
---

```cpp
#include <iostream>
#include <string>
#include <map>
using namespace std;

int main()
{
    map<string, string> m;      // <key, data>

    pair<string, string> p1("월요일", "mon");
    m.insert(p1);

    m.insert(make_pair("화요일", "tue"));

    m["수요일"] = "wed";

    cout << m["월요일"] << endl;        // "mon"
    cout << m["토요일"] << endl;        // 새로운 pair가 생성되어 버린다.!!

    auto ret = m.find("월요일");
    if(ret == m.end())
        cout << "fail" << endl;
}
```

```cpp
#include <iostream>
#include <string>
#include <map>
using namespace std;

int main()
{
    map<int, string> m;

    m[1] = "ONE";
    m[0] = "ZERO";
    m[2] = "TWO";

    auto p = begin(m);

    cout << p->first << endl;       // 0
    cout << p->second << endl;      // "ZERO"
}
```

```cpp

```

