---
title: "(C++) Nested Template Classes"
permalink: cpp/nest-template/                # link 직접 지정
#toc: true                       # for Sub-title (On this page)
comments: true                  # for disqus Comments
categories:                     # for categories
date: 2020-09-20 00:00:00 -0000
last_modified_at: 2020-09-20 00:00:00 -0000
sidebar:
  title: "목차"
  nav: cpp
tag:
  - cpp
category:
  - Nested Template Classes
classes: wide
excerpt: ""
header:
  teaser: /file/image/cpp-page-teaser.gif
---

```cpp
// 아래와 같은 기능이 가능하게 ring class를 구현해보자
#include "ring.h"

int main() {
    ring<string>::iterator it;

    cout << *it << endl;

    ring<string> textring(3);

    textring.add("one");
    textring.add("two");
    textring.add("three");

    for(int i = 0; i < textring.size(); i ++) {
        cout << textring.get(i) << endl;
    }

    return 0;
}
```

```cpp
#ifndef RING_H_
#define RING_H_

#include <iostream>
using namespace std;

class ring {
public:
    class iterator {
    public:
        void print() {
            cout << "Hellow from iterator" << endl;
        }
    };
};

#endif  // RING_H_
```

```cpp
int main() {
    ring<string>::iterator it;
    it.print();
    // 여기까지는 구현됨.
```

코드를 조금 정리해보자.

```cpp
#ifndef RING_H_
#define RING_H_

#include <iostream>
using namespace std;

class ring {
public:
    class iterator;
};

class ring::iterator {
public:
    void print();
};

void ring::iterator::print() {
    cout << "Hellow from iterator" << endl;
}

#endif  // RING_H_
```

ring의 자료형을 정의해보자

```cpp
#ifndef RING_H_
#define RING_H_

#include <iostream>
using namespace std;

template<class T>
class ring {
public:
    class iterator;
};

template<class T>
class ring<T>::iterator {
public:
    void print();
};

void ring::iterator::print() {
    cout << "Hellow from iterator : " << T() << endl;
}

#endif  // RING_H_
```

---

## A Ring Buffer Classes

위 내용의 연장이다.

```cpp

```