---
title: "(C++) Function Pointer"
permalink: cpp/function-pointer/                # link 직접 지정
#toc: true                       # for Sub-title (On this page)
comments: true                  # for disqus Comments
categories:                     # for categories
date: 2020-09-18 00:00:00 -0000
last_modified_at: 2020-09-18 00:00:00 -0000
sidebar:
  title: "목차"
  nav: cpp
tag:
  - cpp
category:
  - function pointer
classes: wide
excerpt: ""
header:
  teaser: /file/image/cpp-page-teaser.gif
---

```cpp
void test() {
    cout << "Hello" << endl;
}

int main() {
    test();     // 일반적 함수콜은 이렇게 한다.

    // 변수에 함수를 담고 싶다면??
    void (*pTest)();      // 함수를 담을 변수를 만들고
    pTest = test;       // 변수에 함수를 담는다.

    pTest();           // 호출은 이렇게..


    // 보통은 이렇게
    void (*ppTest)() = test;
    ppTest();

    return 0;
}
```

매개변수가 있다면?

```cpp
void test(int _a) {
    cout << "Hello" << endl;
}

void (*pTest)(int) = test;
```