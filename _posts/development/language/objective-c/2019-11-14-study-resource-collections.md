---
title: "[Objective-C] 스터디 리소스 모음"
last_modified_at: 2019-11-14T13:12+09:00
header:
  overlay_color: "#333"
categories:
  - Development/Language/Objective-C
tags:
  - Language
  - Objective-C
---

# 들어가며

내가 iOS 개발에 입문했을 때 공부했던 Objective-C 스터디 리소스를 정리해봤다. 정리하면서 문서를 하나씩 살펴보는데 Objective-C를 집중적으로 공부하고 사용한 지
꽤 오랜 시간이 지난 까닭에 다시금 와닿는 자료들도 있어서 나도 일부 자료는 다시 보고 되새김질을 해야할 것 같다. 😅

그런데 Objective-C와 Foundation을 분리하여 다루기 애매해서 그런지 이 둘을 함께 설명하고 있는 스터디 리소스가 많았다. 그래도 이 둘을 동시에 공부한다면 Objective-C와 Foundation의 차이를 명확히 구분하여 아는 것이 좋다.

Objective-C 언어 자체에서는 클래스 기반의 스트링, 넘버 및 컬렉션 등의 데이터 타입과 네트워크, OS 서비스 등은 지원하지 않기 때문에 앱 구현에 필요한 기본적인 레이어를 정의한 Foundation이라는 별도의 프레임워크를 제공하고 있다.

🌟&nbsp; Objective-C != Foundation 🌟

그리고 나중에 기회가 된다면 도서를 제외한 저작권 이슈가 없는 나머지 리소스들을 번역하고 정리하는 시간도 가져보도록 하겠다.

# 리소스

## 1. 애플 개발자 문서

- [The Objective-C Programming Language](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/ObjectiveC/Introduction/introObjectiveC.html)
- [Programming with Objective-C](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/ProgrammingWithObjectiveC/Introduction/Introduction.html)
- [Concepts in Objective-C Programming](https://developer.apple.com/library/archive/documentation/General/Conceptual/CocoaEncyclopedia/Introduction/Introduction.html#//apple_ref/doc/uid/TP40010810)
- [Objective-C Runtime Programming Guide](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/ObjCRuntimeGuide/Introduction/Introduction.html#//apple_ref/doc/uid/TP40008048)
- [Objective-C Runtime Documentation](https://developer.apple.com/documentation/objectivec/objective-c_runtime)
- [Advanced Memory Management Programming Guide](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/MemoryMgmt/Articles/MemoryMgmt.html#//apple_ref/doc/uid/10000011i)
- [Object-Oriented Programming with Objective-C](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/OOP_ObjC/Introduction/Introduction.html#//apple_ref/doc/uid/TP40005149)

**경고:** 애플 개발자 문서는 언제든지 사라질 수 있음.
{: .notice--warning}

## 2. Clang 11 문서

- [Clang Language Extensions - Objective-C Features](https://clang.llvm.org/docs/LanguageExtensions.html?highlight=objective#objective-c-features)
- [Objective-C Literals](https://clang.llvm.org/docs/ObjectiveCLiterals.html?highlight=objective)
- [Objective-C Automatic Reference Counting (ARC)](https://clang.llvm.org/docs/AutomaticReferenceCounting.html?highlight=objective)
- [Block Implementation Specification - Objective-C Extensions to Blocks](https://clang.llvm.org/docs/Block-ABI-Apple.html?highlight=objective#objective-c-extensions-to-blocks)
- [Language Specification for Blocks - Objective-C Extensions](https://clang.llvm.org/docs/BlockLanguageSpec.html?highlight=objective#objective-c-extensions)

## 3. 도서

- 프로그래밍 오브젝티브-C 2.0, 스티븐 코찬, 인사이트
- 아론 힐리가스의 오브젝티브-C 프로그래밍, 아론 힐리가스, 제이펍
- 오브젝티브 C 개발 레시피, 매튜 켐벨, 길벗
- 오브젝티브-C 핸드북, 하야시 아키라, 위키북스
- OS X 구조를 이해하면서 배우는 Objective-C, 오기하라 타케시, 한빛미디어
- 이펙티브 오브젝티브-C 2.0, 맷 갤러웨이, 인사이트
- 프로 오브젝티브-C 디자인 패턴, 카를로 청, 제이펍
- Cocoa Internals, 김정, 인사이트

## 4. 네이버 모바일 교육

- [iOS 앱개발 초급](https://tv.naver.com/v/364932/list/33493)
- [iOS 앱개발 문제해결 중급](https://tv.naver.com/v/384067/list/35318)

# Hacoma's Objective-C Series

- [[Objective-C] 원시 데이터형 - Primitive Data Types](https://hacoma.github.io/development/language/objective-c/primitive-data-types/)
- [Objective-C] 연산자와 표현식 - Operators and Expressions
- [Objective-C] 반복문 - Loop Statements
- [Objective-C] 조건문
- [Objective-C] 클래스와 객체, 메서드
- [Objective-C] 상속
- [Objective-C] 다형성과 동적 타이핑, 동적 바인딩
- [Objective-C] 변수와 Access Modifiers
- [Objective-C] 프로퍼티
- [Objective-C] 카테고리와 프로토콜
- [Objective-C] 전처리기
- [Objective-C] 블록
- [Objective-C] Generics
- [Objective-C] Nullability
- [Objective-C] ANSI C

===

부족한 글 읽어주셔서 감사합니다.

잘못된 내용이나 오탈자에 대한 지적은 언제나 환영입니다.  
댓글로 남겨주시면 반영하도록 하겠습니다.
