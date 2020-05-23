---
title: "Modern C++(11이후) 문법"
permalink: /cpp/modern/                # link 직접 지정
toc: true                       # for Sub-title (On this page)
comments: true                  # for disqus Comments
categories:                     # for categories
date: 2020-03-15 00:00:00 -0000
last_modified_at: 2020-03-15 00:00:00 -0000
sidebar:
  title: "C++"
  nav: cpp
---

## 주요사항 정리

* [move 다시 정리](https://goodayth.github.io/cpp-im-re-move/) : r value reference로 메모리를 받고 싶을때
* [perfect forward 다시 정리](https://goodayth.github.io/cpp-im-re-pf/) : 복사 생성없이 매개변수를 전달하고 싶을때
* [함수포인터가 인라인치환이 안되는 이유](https://goodayth.github.io/cpp-im-re-inline/)

## this call

* [this call](https://goodayth.github.io/cpp-im-this-call/)
* [멤버함수 포인터](https://goodayth.github.io/cpp-im-mem-function/)
* [this와 상속](https://goodayth.github.io/cpp-im-this-inheritance/)
* [멤버 변수 포인터](https://goodayth.github.io/cpp-im-mem-var-pointer/)

## const

* [상수 멤버 함수의 필요성](https://goodayth.github.io/cpp-im-const-func/)
* [논리적 상수성](https://goodayth.github.io/cpp-im-logical-const/)

## new

* [new vs operator new](https://goodayth.github.io/cpp-im-new-operator-new/)
* [placement new](https://goodayth.github.io/cpp-im-placement-new/)
* [생성자의 명시적 호출이 필요한 이유](https://goodayth.github.io/cpp-im-new-explicit/)

## 생성자

* [생성자 호출순서](https://goodayth.github.io/cpp-im-constructor-order/)

## trivial

* [trivial 개념](https://goodayth.github.io/cpp-im-trivial-concept/)
* [trivial 활용](https://goodayth.github.io/cpp-im-trivial-use/)
* [trivial 정리](https://goodayth.github.io/cpp-im-trivial/)

## conversion

* [변환 연산자/변환 생성자](https://goodayth.github.io/cpp-im-conversion-constructor/)
* [변환의 장단점](https://goodayth.github.io/cpp-im-conversion-proscons/)
* [explicit](https://goodayth.github.io/cpp-im-explicit/)
* [make nullptr](https://goodayth.github.io/cpp-im-make-nullptr/)
* [return type resolver](https://goodayth.github.io/cpp-im-resolver/)
* [safe bool](https://goodayth.github.io/cpp-im-safe-bool/)
* [Explicit Conversion Operator](https://goodayth.github.io/cpp-im-explicit-conversion/)
* [brace-init & conversion](https://goodayth.github.io/cpp-im-brace-init/)

## constructor

* [delegate constructor](https://goodayth.github.io/cpp-im-delegate-constructor/)
* [inherit constructor](https://goodayth.github.io/cpp-im-inherit-constructor/)

## initializer(초기화)

* [초기화 코드의 문제](https://goodayth.github.io/cpp-im-initializer/)
* [uniform initialization](https://goodayth.github.io/cpp-im-uniform-initialization/)
* [copy vs direct initialization](https://goodayth.github.io/cpp-im-copy-direct-initialization/)
* [default vs value initialization](https://goodayth.github.io/cpp-im-default-value-initialization/)
* [aggregate initialization](https://goodayth.github.io/cpp-im-aggregate-initialization/)
* [초기화 코드의 문제 해결](https://goodayth.github.io/cpp-im-initialization2/)

## auto / decltype

* [auto](https://goodayth.github.io/cpp-im-auto/)
* [decltype](https://goodayth.github.io/cpp-im-decltype/)
* [auto / decltype 정리](https://goodayth.github.io/cpp-im-auto-decltype/)

## 임시객체

* [임시객체의 개념과 수명](https://goodayth.github.io/cpp-im-temporary-object/)
* [임시객체와 함수](https://goodayth.github.io/cpp-im-temporary-object-function/)
* [참조리턴 vs 값리턴](https://goodayth.github.io/cpp-im-temporary-object-return/)
* [임시객체가 생성되는 다양한 경우](https://goodayth.github.io/cpp-im-temporary-object-make/)
* [임시객체와 멤버함수](https://goodayth.github.io/cpp-im-temporary-object-func/)

## l, r value

* [lvalue와 rvalue](https://goodayth.github.io/cpp-im-lvalue-rvalue/)
* [연산자와 lvalue](https://goodayth.github.io/cpp-im-lvalue/)
* [rvalue reference](https://goodayth.github.io/cpp-im-rvalue-reference/)
* [reference collapse](https://goodayth.github.io/cpp-im-reference-collapse/)
* [forwarding reference](https://goodayth.github.io/cpp-im-forwarding-reference/)

## move semantics

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

## perfect forwarding

* [perfect forwarding 개념](https://goodayth.github.io/cpp-im-perfect-forwarding/)
* [perfect forwarding 구현](https://goodayth.github.io/cpp-im-perfect-forwarding-make/)
* [forwarding reference](https://goodayth.github.io/cpp-im-forwarding-reference/)
* [chronometry 함수 완성](https://goodayth.github.io/cpp-im-chronometry-func/)
* [using perfect forwarding](https://goodayth.github.io/cpp-im-using-perfect-forwarding/)
* [std::forward 구현해보기](https://goodayth.github.io/cpp-im-make-std-forward/)
* [setter using move & copy](https://goodayth.github.io/cpp-im-make-move-copy-setter/)

## reference wrapper

* [std::bind](https://goodayth.github.io/cpp-im-bind/)
* [reference_wrapper](https://goodayth.github.io/cpp-im-reference-wrapper/)

## inline

* [inline function](https://goodayth.github.io/cpp-im-inline-func/)

## functor

* [function object](https://goodayth.github.io/cpp-im-function-object/)
* [function vs functor](https://goodayth.github.io/cpp-im-function-functor/)
* [상태를 가지는 함수](https://goodayth.github.io/cpp-im-function-state/)
* [최종정리](https://goodayth.github.io/cpp-im-functor-final/)

## Lambda Expression & Closure Object

* [Closure Object](https://goodayth.github.io/cpp-im-closure/)
* [lambda expression & type](https://goodayth.github.io/cpp-im-lambda-type/)
* [lambda & function argument](https://goodayth.github.io/cpp-im-lambda-argument/)
* [lambda & suffix return type](https://goodayth.github.io/cpp-im-lambda-return/)

## Capturing Variable

* [Capture Variable](https://goodayth.github.io/cpp-im-capture-variable/)
* [Conversion](https://goodayth.github.io/cpp-im-conversion/)
* [MISC](https://goodayth.github.io/cpp-im-lambda-misc/)
* [advanced lambda](https://goodayth.github.io/cpp-im-lambda-advanced/)

## Callable Object & invoke

* [Callable Object & invoke](https://goodayth.github.io/cpp-im-callable-object/)

## 기타

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