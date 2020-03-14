---
title: "C++ 목차"
permalink: /cpp/                # link 직접 지정
toc: true                       # for Sub-title (On this page)
comments: true                  # for disqus Comments
categories:                     # for categories
date: 2020-03-15 00:00:00 -0000
last_modified_at: 2020-03-15 00:00:00 -0000
sidebar:
  title: "C++ 목차"
  nav: cpp
---

## C++ Basic

* [간단하지만 잘 몰랐던 부분](https://goodayth.github.io/cpp-basic/)
* [decltype](https://goodayth.github.io/decltype/)
* [const와 constexpr](https://goodayth.github.io/const_constexpr/)
* [delete 함수삭제](https://goodayth.github.io/cpp-delete/)
* [suffix 후위리턴](https://goodayth.github.io/cpp-suffix/)
* [Explicit casting 명시적형변환](https://goodayth.github.io/cpp-explicit-casting/)
* [friend 함수](https://goodayth.github.io/cpp-friend-func/)
* [생성자, 소멸자 호출순서](https://goodayth.github.io/cpp-newdel-call/)
* [up/down casting](https://goodayth.github.io/cpp-up-down-casting/)
* [RTTI](https://goodayth.github.io/cpp-RTTI/)
* [mutable](https://goodayth.github.io/cpp-mutable/)
* [상수 멤버 함수](https://goodayth.github.io/cpp-const-func/)
* [static memeber](https://goodayth.github.io/cpp-static-member/)
* [연산자 재정의](https://goodayth.github.io/cpp-operator/)
* [STL 컨테이너](https://goodayth.github.io/cpp-STL/)
* [exception](https://goodayth.github.io/cpp-exception/)
* [함수오버로딩](https://goodayth.github.io/cpp-function-overloading/)
* [가변인자(Variadic Template)](https://goodayth.github.io/cpp-variadic-template/)

---

## C++ OOP & Design Pattern

### Section 1. : Warming Up

* [protected constructor](https://goodayth.github.io/cpp-dp-protected-constructor/)
* [upcasting](https://goodayth.github.io/cpp-dp-upcasting/)
* [abstract class, interface & coupling](https://goodayth.github.io/cpp-dp-coupling/)
* [예제](https://goodayth.github.io/cpp-dp-example/)

### Section 2. : 공통성과 가변성의 분리

* [edit control 만들기](https://goodayth.github.io/cpp-dp-s2-1/)
* [변하는 것을 다른 클래스로](https://goodayth.github.io/cpp-dp-s2-3/) : template Pattern, Strategy Pattern 비교
* [Policy Base Design](https://goodayth.github.io/cpp-dp-s2-4/) : Strategy Pattern, Policy Base Pattern 비교
* [Application Framework](https://goodayth.github.io/cpp-dp-s2-5/) : template pattern 사용 대표 예시
* [함수와 정책](https://goodayth.github.io/cpp-dp-s2-6/) : Strategy Pattern을 함수에 적용
* [state pattern](https://goodayth.github.io/cpp-dp-s2-7/) : 오브젝트의 함수(동작)만 수정하고 싶을때 사용하는 패턴 -> Strategy pattern과 동일

* 정리 : 변하지 않는 코드에서 변해야 하는 부분은 분리하자
    - 일반 함수에서 변한다면? -> 함수 인자로 분리(함수 포인터, 함수객체, 람다 표현식)
    - 멤버 함수에서 변한다면?
        - 가상 함수로 분리 -> template pattern
            - 실행시간에 교체할 수 없고, 변하는 코드를 재사용할 수 없다.
        - 상속기반의 패턴
        - 다른 클래스로 분리 -> Strategy, Policy Base Design
        - 인터페이스로 교체 -> Strategy
            - 실행시간 교체가능, 가상함수 기반(느리다.)
        - 템플릿 인자로 교체 -> Policy Base Design
            - 실행시간 교체불간으, 인라인 치환 가능(빠르다)

### Section 3. : 재귀적 포함

* [Composite Pattern](https://goodayth.github.io/cpp-dp-s3-1/) : Menu 구현을 통한 Composite Pattern 설명
* [Menu Event](https://goodayth.github.io/cpp-dp-s3-2/) : Menu Command 처리, 일반/멤버 함수 포인터 처리 ,function 템플릿 사용법
* [Decorator](https://goodayth.github.io/cpp-dp-s3-3/) : Decorator pattern 설명

### Section 4. 간접층의 원리

* [Adapter](https://goodayth.github.io/cpp-dp-s4-1/) : stack, reverse_iterator
* [Proxy](https://goodayth.github.io/cpp-dp-s4-2/)
* [Facade](https://goodayth.github.io/cpp-dp-s4-3/)
* [Bridge](https://goodayth.github.io/cpp-dp-s4-4/)

* 정리 : 해결하기 어려운 문제를 간접층을 도입해서 해결하는 방법을 설명한다.
    - 인터페이스 변경 : Adapter
    - 대행자 : Proxy
    - 서브시스템 복잡한 과정을 숨긴다 : Facade
    - Update를 독맂벅으로 수행 : Bridge

### Section 5. : 통보, 열거, 방문

* [Observer](https://goodayth.github.io/cpp-dp-s5-1/)
* [Container](https://goodayth.github.io/cpp-dp-s5-2/)
* [Iterator](https://goodayth.github.io/cpp-dp-s5-3/)
* [Visitor](https://goodayth.github.io/cpp-dp-s5-4/) : 오브젝트에 함수를 추가한 효과를 내고 싶다

### Section 6. : 객체를 생성하는 방법

* [객체를 생성하는 방법](https://goodayth.github.io/cpp-dp-s6-1/)
* [Singleton](https://goodayth.github.io/cpp-dp-s6-2/)
* [Factory](https://goodayth.github.io/cpp-dp-s6-3/)
* [Abstract Factory](https://goodayth.github.io/cpp-dp-s6-4/)
* [Factory Method](https://goodayth.github.io/cpp-dp-s6-5/)
* [Builder](https://goodayth.github.io/cpp-dp-s6-6/)

---

## C++ Intermediate

### 주요사항 정리

* [move 다시 정리](https://goodayth.github.io/cpp-im-re-move/) : r value reference로 메모리를 받고 싶을때
* [perfect forward 다시 정리](https://goodayth.github.io/cpp-im-re-pf/) : 복사 생성없이 매개변수를 전달하고 싶을때
* [함수포인터가 인라인치환이 안되는 이유](https://goodayth.github.io/cpp-im-re-inline/)

### this call

* [this call](https://goodayth.github.io/cpp-im-this-call/)
* [멤버함수 포인터](https://goodayth.github.io/cpp-im-mem-function/)
* [this와 상속](https://goodayth.github.io/cpp-im-this-inheritance/)
* [멤버 변수 포인터](https://goodayth.github.io/cpp-im-mem-var-pointer/)

### const

* [상수 멤버 함수의 필요성](https://goodayth.github.io/cpp-im-const-func/)
* [논리적 상수성](https://goodayth.github.io/cpp-im-logical-const/)

### new

* [new vs operator new](https://goodayth.github.io/cpp-im-new-operator-new/)
* [placement new](https://goodayth.github.io/cpp-im-placement-new/)
* [생성자의 명시적 호출이 필요한 이유](https://goodayth.github.io/cpp-im-new-explicit/)

### 생성자

* [생성자 호출순서](https://goodayth.github.io/cpp-im-constructor-order/)

### trivial

* [trivial 개념](https://goodayth.github.io/cpp-im-trivial-concept/)
* [trivial 활용](https://goodayth.github.io/cpp-im-trivial-use/)
* [trivial 정리](https://goodayth.github.io/cpp-im-trivial/)

### conversion

* [변환 연산자/변환 생성자](https://goodayth.github.io/cpp-im-conversion-constructor/)
* [변환의 장단점](https://goodayth.github.io/cpp-im-conversion-proscons/)
* [explicit](https://goodayth.github.io/cpp-im-explicit/)
* [make nullptr](https://goodayth.github.io/cpp-im-make-nullptr/)
* [return type resolver](https://goodayth.github.io/cpp-im-resolver/)
* [safe bool](https://goodayth.github.io/cpp-im-safe-bool/)
* [Explicit Conversion Operator](https://goodayth.github.io/cpp-im-explicit-conversion/)
* [brace-init & conversion](https://goodayth.github.io/cpp-im-brace-init/)

### constructor

* [delegate constructor](https://goodayth.github.io/cpp-im-delegate-constructor/)
* [inherit constructor](https://goodayth.github.io/cpp-im-inherit-constructor/)

### initializer(초기화)

* [초기화 코드의 문제](https://goodayth.github.io/cpp-im-initializer/)
* [uniform initialization](https://goodayth.github.io/cpp-im-uniform-initialization/)
* [copy vs direct initialization](https://goodayth.github.io/cpp-im-copy-direct-initialization/)
* [default vs value initialization](https://goodayth.github.io/cpp-im-default-value-initialization/)
* [aggregate initialization](https://goodayth.github.io/cpp-im-aggregate-initialization/)
* [초기화 코드의 문제 해결](https://goodayth.github.io/cpp-im-initialization2/)

### auto / decltype

* [auto](https://goodayth.github.io/cpp-im-auto/)
* [decltype](https://goodayth.github.io/cpp-im-decltype/)
* [auto / decltype 정리](https://goodayth.github.io/cpp-im-auto-decltype/)

### 임시객체

* [임시객체의 개념과 수명](https://goodayth.github.io/cpp-im-temporary-object/)
* [임시객체와 함수](https://goodayth.github.io/cpp-im-temporary-object-function/)
* [참조리턴 vs 값리턴](https://goodayth.github.io/cpp-im-temporary-object-return/)
* [임시객체가 생성되는 다양한 경우](https://goodayth.github.io/cpp-im-temporary-object-make/)
* [임시객체와 멤버함수](https://goodayth.github.io/cpp-im-temporary-object-func/)

### l, r value

* [lvalue와 rvalue](https://goodayth.github.io/cpp-im-lvalue-rvalue/)
* [연산자와 lvalue](https://goodayth.github.io/cpp-im-lvalue/)
* [rvalue reference](https://goodayth.github.io/cpp-im-rvalue-reference/)
* [reference collapse](https://goodayth.github.io/cpp-im-reference-collapse/)
* [forwarding reference](https://goodayth.github.io/cpp-im-forwarding-reference/)

### move semantics

* [복사생성자의 모양](https://goodayth.github.io/cpp-im-copy-constructor/)
* [move sematics](https://goodayth.github.io/cpp-im-move-sematics/)
* [std::move](https://goodayth.github.io/cpp-im-move/)
* [using move](https://goodayth.github.io/cpp-im-move-using/)
* [move & noexcept](https://goodayth.github.io/cpp-im-move-noexcept/)
* [move를 활용한 버퍼 복사](https://goodayth.github.io/cpp-im-move-buffer-copy/)
* [std::move 만들기](https://goodayth.github.io/cpp-im-move-make/)
* [move와 const object](https://goodayth.github.io/cpp-im-move-const-object/)
* [move 생성자 만들기](https://goodayth.github.io/cpp-im-move-constructor-make/)
* [value categories](https://goodayth.github.io/cpp-im-move-value-categories/)

### perfect forwarding

* [perfect forwarding 개념](https://goodayth.github.io/cpp-im-perfect-forwarding/)
* [perfect forwarding 구현](https://goodayth.github.io/cpp-im-perfect-forwarding-make/)
* [forwarding reference](https://goodayth.github.io/cpp-im-forwarding-reference/)
* [chronometry 함수 완성](https://goodayth.github.io/cpp-im-chronometry-func/)
* [using perfect forwarding](https://goodayth.github.io/cpp-im-using-perfect-forwarding/)
* [std::forward 구현해보기](https://goodayth.github.io/cpp-im-make-std-forward/)
* [setter using move & copy](https://goodayth.github.io/cpp-im-make-move-copy-setter/)

### reference wrapper

* [std::bind](https://goodayth.github.io/cpp-im-bind/)
* [reference_wrapper](https://goodayth.github.io/cpp-im-reference-wrapper/)

### inline

* [inline function](https://goodayth.github.io/cpp-im-inline-func/)

### functor

* [function object](https://goodayth.github.io/cpp-im-function-object/)
* [function vs functor](https://goodayth.github.io/cpp-im-function-functor/)
* [상태를 가지는 함수](https://goodayth.github.io/cpp-im-function-state/)
* [최종정리](https://goodayth.github.io/cpp-im-functor-final/)

### Lambda Expression & Closure Object

* [Closure Object](https://goodayth.github.io/cpp-im-closure/)
* [lambda expression & type](https://goodayth.github.io/cpp-im-lambda-type/)
* [lambda & function argument](https://goodayth.github.io/cpp-im-lambda-argument/)
* [lambda & suffix return type](https://goodayth.github.io/cpp-im-lambda-return/)

### Capturing Variable

* [Capture Variable](https://goodayth.github.io/cpp-im-capture-variable/)
* [Conversion](https://goodayth.github.io/cpp-im-conversion/)
* [MISC](https://goodayth.github.io/cpp-im-lambda-misc/)
* [advanced lambda](https://goodayth.github.io/cpp-im-lambda-advanced/)

### Callable Object & invoke

* [Callable Object & invoke](https://goodayth.github.io/cpp-im-callable-object/)

### 기타

* [name mangling](https://goodayth.github.io/cpp-im-name-mangling/)
* [함수이름과 함수주소](https://goodayth.github.io/cpp-im-func-name-add/)
* [함수 찾는 순서](https://goodayth.github.io/cpp-im-func-order/)
* [using](https://goodayth.github.io/cpp-im-using/)
* [static_assert](https://goodayth.github.io/cpp-im-static-assert/)
* [begin/end](https://goodayth.github.io/cpp-im-begin-end/)
* [ranged-for](https://goodayth.github.io/cpp-im-ranged-for/)
* [delete function](https://goodayth.github.io/cpp-im-delete-function/)
* [noexcept](https://goodayth.github.io/cpp-im-noexcept/)
* [scoped enum](https://goodayth.github.io/cpp-im-scoped-enum/)
* [user define literal](https://goodayth.github.io/cpp-im-user-define-literal/)
* [if-init, if-constexpr](https://goodayth.github.io/cpp-im-if-init-constexpr/)
* [structure binding](https://goodayth.github.io/cpp-im-structure-binding/)
* [initializer_list](https://goodayth.github.io/cpp-im-initializer_list/)
* [배열의 이름은 배열의 주소일까?](https://goodayth.github.io/cpp-im-array-name/)

---

## C++ 문법 정리

* [define문에서 ##](https://goodayth.github.io/cpp-define)
* [next_permutation](https://goodayth.github.io/C++-next_permutation) : 순열(permutation) 사용하기
* [const char *& VS const char * 차이점](https://goodayth.github.io/C++-constchar/)
* [vector sorting](https://goodayth.github.io/C++-vector-sorting/)
* [string to int](https://goodayth.github.io/C++-string-to-int/)
* [GetTickCount](https://goodayth.github.io/cpp-gettickcount/)

## thread

* [thread](https://goodayth.github.io/cpp-thread/)

---

## Design Pattern

* [옵저버 패턴(Observer Pattern)](https://goodayth.github.io/cpp-design-observer/)
* [팩토리 패턴(Factory Pattern)](https://goodayth.github.io/cpp-design-factory/)

---

## 코딩 테스트

* [int배열 사이즈 출력]()

```cpp
int m_array = {0, 1, 2, 3};
int m_array_size = sizeof(m_array) / sizeof(int);
```

### 문자열 파싱

* [문자열파싱](https://goodayth.github.io/C++-parsing/)
* [A-B 문자열에서 A,B파싱](https://goodayth.github.io/C++-parsing-A-B/)
* [문자열 파싱 (A-B)(C-D)라는 문자열에서 A,B,C,D파싱](https://goodayth.github.io/C++-parsing-(A-B)(C-D)/)
* [Transitivity Relations](https://goodayth.github.io/C++-Transitivity-Relations/)

---

### 좋은문제

* [pattern 찾기](https://goodayth.github.io/C++-Quize-pattern/)
* [LCS Algorithm 만들기](https://goodayth.github.io/C++-LCS/)
* [Dijkstra Algorithm 만들기](https://goodayth.github.io/C++-Dijkstra/)

---

### 기타

* [String Array 길이 찾기](https://goodayth.github.io/C++-string-array-length/)
* [int형 2차 배열 사용하기](https://goodayth.github.io/C++-int-2D-array-use/)
* [2차원 string 배열의 문자열을 파싱해서 2차원 int형 배열로 넣기](https://goodayth.github.io/C++-2D-array-example/)
* [map과 vector, class 잘 사용하기](https://goodayth.github.io/C++-using-map/)

