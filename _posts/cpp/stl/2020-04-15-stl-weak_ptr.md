---
title: "STL : weak_ptr"
permalink: cppstl/spointer/weak_ptr/                # link 직접 지정
toc: true                       # for Sub-title (On this page)
comments: true                  # for disqus Comments
categories:                     # for categories
date: 2020-04-15 00:00:00 -0000
last_modified_at: 2020-04-15 00:00:00 -0000
sidebar:
  title: "C++"
  nav: cpp
---

## 1

* [Run This Code](https://ideone.com/W37Jft)

```cpp
#include <iostream>
#include <string>
#include <memory>
using namespace std;

struct People
{
    People(string s) : name(s) {}
    ~People() { cout << "~People : " << name << endl; }

    string name;
    shared_ptr<People> bf;  // best friend
};

int main()
{
    shared_ptr<People> p1(new People("Kim"));
    shared_ptr<People> p2(new People("Lee"));

    p1->bf = p2;
    p2->bf = p1;
    // 자원이 파괴되지 않는다.
    // 서로가 서로를 가르키게 된다.
}
```

* 참조변수가 증가하지 않는 포인터가 필요하다

* [Run This Code]()

```cpp
#include <iostream>
#include <string>
#include <memory>
using namespace std;

struct People
{
    People(string s) : name(s) {}
    ~People() { cout << "~People : " << name << endl; }

    string name;
    weak_ptr<People> bf;  
    // 참조변수가 증가하지 않는 포인터가 필요
    // 또한 원본 객체가 파괴되었는지 알수도 있다!!
};
```

* [Run This Code](https://ideone.com/E0QsI2)

```cpp
#include <iostream>
#include <memory>
using namespace std;

class Car
{
    int color;
    int speed;
public:
    ~Car() { cout << "~Car()" << endl; }
 
    void Go() { cout << "Car go" << endl; }
};

int main()
{
    shared_ptr<Car> wp; // use count 증가
    shared_ptr<Car> sp(new Car);
    wp = sp;

    cout << sp.use_count() << endl; // 2
```

* [Run This Code](https://ideone.com/6jdUwU)

```cpp
int main()
{
    weak_ptr<Car> wp; // use count 증가 X
    
    {
        shared_ptr<Car> sp(new Car);
        wp = sp;

        cout << sp.use_count() << endl; // 1
    }

    if( wp.expired() )
        cout << "destory" << endl;
    else
        cout << "not destory" << endl;
```

* [Run This Code](https://ideone.com/32jsAX)

```cpp
int main()
{
    weak_ptr<Car> wp; // use count 증가 X
    
    //{
        shared_ptr<Car> sp(new Car);
        wp = sp;

        cout << sp.use_count() << endl; // 1
    //}

    if( wp.expired() )
        cout << "destory" << endl;
    else {
        cout << "not destory" << endl;
        wp->Go();       // error - weak_ptr은 대상 객체에 접근 불가
        // 이유는 use_count를 쓰지 않기에 다른곳에서 모르고 삭제를 해 버릴수 있다. 그런 실수를 방지하기 위해서 weak_ptr은 직접접근 불가

        // weak_ptr을 가지고 다시 shared_ptr을 만들어야한다.
    }
```

```cpp
shared_ptr<Car> sp2 = wp.lock();

if(sp2)
    sp->Go();
```