---
title: "[Objective-C] 연산자와 표현식 - Operators and Expressions"
last_modified_at: 2019-11-18T13:12+09:00
header:
  overlay_color: "#333"
categories:
  - Development/Language/Objective-C
tags:
  - Language
  - Objective-C
---

# 주의

본 글은 `Objective-C 2.0` 기준으로 작성되었다.

# 들어가며

Objective-C에서 제공하는 연산자와 표현식을 알아보기 전에 우리는 대학교에서 프로그래밍언어론과 컴파일러론을 수강했던 기억을 떠올려보도록 하겠다.
대부분의 컴파일러는 아래와 같은 일련의 컴파일 과정을 거치게 된다고 배웠다.

- 어휘 분석 (lexical analyze)
- 구문 분석 (syntax analyze)
- 의미 분석 (semantic analyze)
- IR 생성 (intermediate representation)
- 최적화 (optimization)
- 코드 생성 (code generation)

LL 파싱, LR 파싱, SLR 파싱, 클로저, 논터미널 등 학교에서 컴파일러론을 공부할 때 머리가 좋지 않아서 고생을 많이 했었는데 조금이나마 기억이 나는 것을 보면 헛수고는 아니였던 것 같다 😅

위의 과정 중 어휘 분석, 구문 분석, 의미 분석 단계에서는 심볼 테이블을 활용하여 토큰과 파스 트리, 추상 구문 트리를 생성하고 문법적 혹은 의미적으로 프로그래밍 언어의 정의에 부합하는지 검사를 하게 된다.
보통 여기까지의 과정을 컴파일러의 Front-end로 볼 수 있는데 Objective-C는 `LLVM`의 Front-end인 `Clang`을 통하여 이러한 과정을 수행하게 된다.

우리는 클랭 형님께서 우리가 작성한 표현식을 잘 분석하시고 노여워하시지 않도록 정해진 규칙에 따라 프로그램을 작성해야 한다. Objective-C의 연산자와 표현식을 정리하는 글에 왠 컴파일러 이야기냐 하겠지만
필요 이상으로 복잡하거나 중첩된 연산식과 표현식은 컴파일 성능에 많은 영향을 줄 수도 있기 때문에 이를 고려해서 최대한 간단 명료하게 연산자와 표현식을 사용하는 것도 중요하다.

그럼 지금부터 Objective-C의 연산자와 표현식을 정리해보도록 하겠다.

# 한번 알아보자

## 1. 표현식 (Expressions)

Objective-C의 기본적인 표현식은 아래와 같이 연산자와 2개의 피연산자, 한 개의 할당으로 구성된다.

```objectivec
int price = 10 + 20;
```

`int` : 데이터형  
`price` : 변수명  
`=` : 할당 연산자  
`10` : 피연산자 1  
`+` : 산술 연산자  
`20` : 피연산자 2  
`;` : statement separator

## 2. 연산자 (Operators)

### (1) 할당 연산자 (Assignment Operator)

할당 연산자는 연산자 기준 오른쪽에 있는 어떠한 값이나 어떠한 값들의 연산 결과를 연산자의 왼쪽에 있는 변수에 할당한다.

```objectivec
// price에 10과 20을 더한 30이 대입
int price = 10 + 20;

// price에 12가 대입
price = 12; 
```

### (2) 산술 연산자 (Arithmetic Operators)

산술 연산자는 더하기, 빼기, 나누기, 곱하기, 나머지 연산 등 수학식을 작성하기 위한 연산자이다.
단항 또는 이항 연산자로 사용할 수 있다.

```objectivec
int price = 10;

// 부호 반전
price = -price;

// 더하기
price = 13 + 20;

// 빼기
price = 10 - 27;

// 곱하기
price = 12 * 20;

// 나누기
price = 11 / 9;

// 나머지 연산
price = 3 % 2;
```

### (3) 복합 할당 연산자 (Compound Assignment Operators)

복합 할당 연산자는 비트 연산자나 산술 연산자가 할당 연산자와 결합된 형태이다.

```objectivec
int price;

// price = price + 13;
price += 13;

// price = price - 10;
price -= 10;

// price = price * 12;
price *= 12;

// price = price / 9;
price /= 9;

// price = price % 3;
price %= 3;

// price = price & 10;
price &= 10;

// price = price | 12;
price |= 12;

// price = price ^ 29;
price ^= 29;

// price = price << 17;
price <<= 17;

// price = price >> 71;
price >>= 71;
```

### (4) 증감 연산자 (Increment and Decrement Operators)

증감 연산자는 피연산자의 값을 1만큼 증가시키거나 감소시키는 용도로 사용된다.
전위 및 후위에 따라서 의도한 결과가 달라질 수도 있으므로 주의해서 사용해야 한다.

```objectivec
// 11 출력
int price1 = 10;
NSLog(@"%d", ++price1);

// 10 출력
int price2 = 10;
NSLog(@"%d", price2++);

// 9 출력
int price3 = 10;
NSLog(@"%d", --price3);

// 10 출력
int price4 = 10;
NSLog(@"%d", price4--);
```

### (5) 비교 연산자 (Comparison Operators)

비교 연산자는 단어 그대로 주어진 두 개의 피연산자를 비교하는 것에 사용된다.

```objectivec
int price1 = 10;
int price2 = 12;

// result1 = YES
BOOL result1 = price1 != price2;

// result2 = NO
BOOL result2 = price1 == price2;

// result3 = NO
BOOL result3 = price1 > price2;

// result4 = YES
BOOL result4 = price1 < price2;

// result5 = NO
BOOL result5 = price1 >= price2;

// result6 = YES
BOOL result6 = price1 <= price2;
```

### (6) 논리 연산자 (Boolean Logical Operators)

논리 연산자도 단어 그대로 주어진 피연산자에 대한 논리 연산을 제공한다. 왼쪽에 있는 피연산자의 컨디션에 따라서 다음에 오는 피연산자에 대한 컨디션 확인을 하지 않을 수도 있다. (Short Circuit Evaluation)

```objectivec
BOOL condition1 = NO;
BOOL condition2 = YES;

// result1 = NO
BOOL result1 = condition1 && condition2;

// result2 = YES
BOOL result2 = condition1 || condition2;

// result3 = YES
BOOL result3 = !condition1;
```

### (7) 삼항 연산자 (The Ternary Operators)

삼항 연산자는 `?` 전까지의 주어진 컨디션을 보고 컨디션이 참이면 참된 표현식, 거짓이면 거짓 표현식을 채택한다.

```objectivec
int price1 = 20;
int price2 = 10;

// max = price1
int max = price1 > price2 ? price1 : price2;
```

op1 `?:` op2 형태로도 사용할 수 있는데 op1이 참이라면 op1, 거짓이라면 op2를 채택한다.

```objectivec
BOOL condition1 = YES;
BOOL condition2 = NO;

// result = condition1
BOOL result = condition1 ?: condition2;
```

### (8) 비트 연산자 (Bitwise Operators)

비트 연산자는 데이터의 이진 연산을 제공한다.

```objectivec
int price1 = 21;
int price2 = 11;

// BCD CDOE (8421)
// 21 = 0001 0101
// 11 = 0000 1011

// result1 = 0000 0001
int result1 = price1 & price2;

// result2 = 0001 1111
int result2 = price1 | price2;

// result3 = 0001 1110
int result3 = price1 ^ price2;

// result4 = 1110 1010
int result4 = ~price1;

// result5 = 0010 1010
int result5 = price1 << 1;

// result6 = 0000 1010
int result6 = price1 >> 1;
```

## 3. 결합 방향 (Associativity)

|Category|Operator|Associativity|
|---|---|---|
|Postfix|() [] -> . ++ \-\-|Left to right|
|Unary|+ - ! ~ ++ \-\- (type)* & sizeof|Right to left|
|Multiplicative|* / %|Left to right|
|Additive|+ -|Left to right|
|Shift|<< >>|Left to right|
|Relational|< <= > >=|Left to right|
|Equality|== !=|Left to right|
|Bitwise AND|&|Left to right|
|Bitwise XOR|^|Left to right|
|Bitwise OR|\||Left to right|
|Logical AND|&&|Left to right|
|Logical OR|\|\||Left to right|
|Conditional|?:|Right to left|
|Assignment|= += -= *= /= %= >>= <<= &= ^= \|=|Right to left|
|Comma|,|Left to right|

우선 순위가 가장 높은 연산자를 표의 제일 상단에 두었으며 하단으로 내려갈수록 우선 순위는 점점 낮아진다. 연산자들 중에 우선 순위가 제일 높은 것을 먼저 평가한다.

# 참조

- [Techotopia Post](https://www.techotopia.com/index.php/Objective-C_Operators_and_Expressions)
- [Tutorialspoint Post](https://www.tutorialspoint.com/objective_c/objective_c_operators.htm)
- [Codescracker Post](https://codescracker.com/objective-c/objective-c-operators.htm)

===

부족한 글 읽어주셔서 감사합니다.

잘못된 내용이나 오탈자에 대한 지적은 언제나 환영입니다.  
댓글로 남겨주시면 반영하도록 하겠습니다.
