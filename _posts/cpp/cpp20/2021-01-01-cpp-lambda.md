---
title: "(c++20) lambda"
permalink: cpp/cpp20/lambda/                # link 직접 지정
#toc: true                       # for Sub-title (On this page)
comments: true                  # for disqus Comments
categories:                     # for categories
date: 2021-01-01 00:00:00 -0000
last_modified_at: 2021-01-01 00:00:00 -0000
sidebar:
  title: "목차"
  nav: cpp
tag:
  - cpp
  - c++20
category:
  - lambda
classes: wide
excerpt: ""
header:
  teaser: /file/image/cpp-page-teaser.gif
---

## 개발환경

* VS2019 Preview

```s
# 빌드하기
cl 소스이름.cpp /std:c++latest
```

![](/file/image/cpp20-lambda-1.png)

---

## C++20에 추가된 새로운 키워드

* Concept 문법 : `concept`, `requires`
* Coroutine 문법 : `co_await`, `co_return`, `co_yield`
* Module 문법 : `module`, `import`, `export`
* 상수성 지원 : `constinit`, `consteval`
* UTF-8 문자 : `char8_t`

---

## Example

```cpp
#include <iostream>
#include <numbers>  // c++20 최신 헤더

int main()
{
  std::cout << std::numbers::pi << std::endl;
  std::cout << std::numbers::e << std::endl;
  std::cout << std::numbers::sqrt2 << std::endl;
}
```

![](/file/image/cpp20-lambda-2.png)

굳이 define하지 않아도 된다.

---

## feature test macro

* 현재 사용중인 컴파일러가 특정 문법 또는 라이브러리 지원여부를 확인가능

```cpp
#include <iostream>
#include <span>
#include <chrono>

int main()
{
    // 언어 특징 지원 여부 조사
#ifdef __cpp_concepts
  // concept이라는 문법을 지원
    std::cout << "support concepts" << std::endl;
#endif

#ifdef __cpp_modules
  // modules이라는 문법을 지원
    std::cout << "support modules" << std::endl;
#endif

    // 라이브러리 특정 지원 여부 조사 (헤더필요)
#ifdef __cpp_lib_span
    std::cout << "support span lib" << "std::endl";
#endif

#ifdef __cpp_lib_chrono 
    std::cout << "support chrono lib" << std::endl;
    std::cout << "chrono version : " << __cpp_lib_chrono << std::endl;
    // cout해보면 버전정보를 의미한다.
#endif
}
```

![](/file/image/cpp20-lambda-3.png)