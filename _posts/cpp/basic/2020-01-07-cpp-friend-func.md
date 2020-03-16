---
title: "(C++) friend 함수"
date: 2020-01-07 00:00:00 -0000
---

> 멤버 함수는 아니지만 private 멤버에 접근 할 수 있게 하고 싶을 때 사용
>
> 특정 함수, 클래스에서 접근이 가능하게 하고 싶을때.

```cpp
class Airplane
{
  int color;
  int speed;
  int engineTemp;
  
public:
  int getSpeed() { return speed; }
  // void fixAirplane(Airplane& a);
  friend void fixAirplane(Airplane& a);   // 내부 멤버에 접근가능!
};

void fixAirplane(Airplane& a)
{
  int n = a.engineTemp;   // engineTemp 접근 불가
}
```