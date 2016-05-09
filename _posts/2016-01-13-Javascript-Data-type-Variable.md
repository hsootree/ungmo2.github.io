---
layout: post
title: Javascript Data type & Variable
categories: javascript
tags: []
---

* TOC
{:toc}

# 1. Data Type (자료형)

모든 프로그래밍 언어의 학습은 Data Type(자료형)을 파악하는 것으로부터 시작된다.

자료형은 프로그래밍 언어에서 객체, 정수, 불린 자료형 등 여러 종류의 데이터를 식별하는 분류를 말한다.

최신 ECMAScript 표준(ECMAScript 2015 (6th Edition, ECMA-262) / 2015.06)은 7개의 data type을 정의한다

* 기본 자료형 (primitive data type)
  * `Boolean`
  * `null`
  * `undefined`
  * `Number`
  * `String`
  * `Symbol` (New in ECMAScript 6)
* `Object`

Javascript의 자료형은 크게 기본 자료형(primitive data type)과 Object(객체형, 참조형)으로 가분할 수 있다.

## 1.1 Primitive Data Type (기본자료형)

기본자료형(Primitive data type)의 값은 변경 불가능한 값(immutable value)이다. 또한 이들은 `pass-by-value`이다.

### 1.1.1 Boolean

논리적인 요소를 나타내며 `true`와 `false` 두가지 값을 가질 수 있다. 비어있는 문자열과 `null`, `undefined`, 숫자 0은 `false`로 간주된다.

```javascript
var foo = true;
var bar = false;
```

### 1.1.2 null

null 타입은 딱 한 가지 값, `null` 을 가질 수 있다. JavaScript는 case-sensitive하므로 `null`은 Null, NULL등과 다르다.

Computer science에서 `null`은 의도적으로 기본형(primitives)과 object형 변수에 값이 없다는 것을 명시한 것이다.

```javascript
var foo = 'Lee';
foo = null;  // 값 또는 참조 정보가 제거됨
```

주의할 것은 데이터 형식을 나타내는 문자열을 반환하는 typeof 연산자로 null값은 가진 변수를 연산해 보면 null이 아닌 object가 나온다. 이는 설계상의 문제이다.

```javascript
var foo  = null;
console.log(typeof foo); // object
```

따라서 null 타입 변수인지 확인할 때 typeof 연산자를 사용하면 안되고 일치 연산자(===)를 사용하여야 한다.

```javascript
var foo  = null;
console.log(typeof foo === null); // false
console.log(foo === null);        // true
```

### 1.1.3 undefined

값을 할당하지 않은 변수는 `undefined` 값을 가진다. 즉, 선언은 되었지만 할당된 적이 없는 변수에 접근하거나 존재하지 않는 객체 프로퍼티에 접근할 경우 반환된다.

```javascript
var foo;
console.log(foo); // undefined

foo = {
  name: 'Lee',
  gender: 'male'
}
console.log(foo.bar); // undefined
```

### 1.1.4 Number

C 언어의 경우, 정수형과 실수형을 구분하여 int, long, float, double 등과 같은 다양한 숫자 자료형이 존재한다. 하지만 자바스크립트는 하나의 숫자 자료형만 존재한다.

ECMAScript 표준에 따르면, 숫자 자료형은 배정밀도 64비트 부동 소수점 형 (double-precision 64-bit floating-point format : -(2<sup>53</sup> -1) 와 2<sup>53</sup> -1 사이의 숫자값) 단 하나만 존재한다. 정수만을 표현하기 위한 특별한 자료형(integer type)은 없다.

추가적으로 세가지 의미있는 기호적인 값들도 표현할 수 있다.

* `+/- Infinity`
* `NaN` (not-a-number)

```javascript
var x = 10;    // 정수
var y = 10.12; // 실수
var z = -20;   // 음의 정수

var foo = 42 / -0;
console.log(foo);        // -Infinity
console.log(typeof foo); // number

var bar = 1 * 'string';
console.log(bar);        // NaN
console.log(typeof bar); // number
```

### 1.1.5 String

String(문자열) 타입은 텍스트 데이터를 나타내는데 사용한다. 이는 0개 또는 그 이상의 유니코드(16비트 부호없는 정수 값) 문자들의 집합이다. 문자열은 작은 따옴표('') 또는 큰 따옴표("") 안에 텍스트를 넣어 생성한다.

```javascript
var name = "John Doe";    // Using double quotes
    name = 'John Doe';    // Using single quotes
console.log(typeof name); // string

var answer = "It's alright";          // Single quote inside double quotes
    answer = "He is called 'Johnny'"; // Single quotes inside double quotes
    answer = 'He is called "Johnny"'; // Double quotes inside single quotes
```

C와 같은 언어와는 다르게, 자바스크립트의 문자열은 변경 불가능(immutable) 하다. 이것은 한 번 문자열이 생성되면, 그 문자열을 변경할 수 없다는걸 의미한다.

```javascript
var str = 'string';
console.log(str[0],str[1],str[2],str[3],str[4],str[5]);

str[0] = 'S';
console.log(str); // string
```

문자열은 배열처럼 인덱스를 통해 접근할 수 있다. str[0] = 'S'처럼 이미 생성된 문자열에 새로운 문자를 대입하여 변경시켜도 반영되지 않는다(이때 에러가 발생하지 않는다). 한번 생성된 문자열은 read only로서 수정은 불가하다. 이것을 변경 불가능(immutable)이라 한다.

그러나 새로운 문자열을 할당하는 것은 물론 가능하다. 이는 기존 문자열을 수정하는 것이 아닌 새로운 문자열을 할당하는 것이기 때문이다.

```javascript
var str = 'string';
console.log(str); // string

str = 'String';
console.log(str); // String

str += ' test';
console.log(str); // String test

str.substring(0, 3);
console.log(str); // Str

str = str.toUpperCase();
console.log(str); // STR
```

### 1.1.6 Symbol

ECMAScript 6(Javascript 2015) 에서 추가되었다. Symbol은 유일하고 변경 불가능한 (immutable) 기본값 (primitive value) 이다. 또한, 객체 속성의 key 값으로도 사용될 수 있다. 몇몇 프로그래밍 언어에서는 Symbol을 atom 이라고 부른다. C 언어의 이름있는 열거형 (enum) 과도 비슷하다.

## 1.2 Object (객체형, 참조형)

[객체](http://ungmo2.github.io/javascript/Javascript-Object/)는 데이터와 그 데이터에 관련되는 동작(절차,방법,기능)을 모두 포함할 수 있는 개념적 존재이다. 달리 말해, 이름과 값을 가지는 데이터를 의미하는 속성(property)와 동작을 의미하는 메서드(method)를 포함하고 있는 독립적 주체이다.

자바스크립트는 객체(object)기반의 스크립트 언어이며 자바스크립트를 이루고 있는 거의 “모든 것”은 객체이다. 기본자료형(Primitives)을 제외한 나머지 값들(배열, 함수, 정규표현식 등)은 모두 객체이다.

* 함수 (Function)
* 배열 (Array)
* 날짜 (Date)
* 정규식 (RegExp)

이것들은 모두 객체이다. 또한 객체는 `pass-by-reference`이다

# 2. Variable (변수)

어플리케이션에서 값(value)을 유지할 필요가 있을 때 변수를 사용한다.  

변수는 값을 저장, 조회, 조작(변경)하는 데 사용되며 다른 사용자가 변수의 존재 목적을 쉽게 이해할 수 있도록 의미있는 이름을 지정하여야한다.

```javascript
var score = 100;  // OK
var x = 3;        // NG
```

변수명은 identifier(식별자)로 불리기도 하며 명명 규칙이 존재한다.

* 반드시 영문자(특수문자 제외), underscore ( _ ), 또는 달러 기호($)로 시작하여야 한다. 이어지는 문자에는 숫자(0~9)도 사용할 수 있다.  
* JavaScript는 대/소문자를 구별하므로 사용할 수 있는 문자는 "A" ~ "Z" (대문자)와 "a" ~ "z" (소문자)이다.

변수를 선언할 때 `var` keyword가 사용된다. 등호(=, equal sign)는 변수에 값을 할당하기 위해 사용된다.

```javascript
var name;     // 변수 name 선언
name = 'Lee'; // 변수 name에 값 'Lee'가 저장(할당)되었다.

var age = 30; // 선언과 할당

var person = "John Doe",
    carName = "Volvo",
    price = 200;

var price = 10;
var tax   = 1;
var total = price + tax;
```

초기화되지 않은 변수는 `undefined` 값을 갖게 된다. 미선언 변수에 접근하면 `ReferenceError` 예외가 발생한다.

```javascript
var x;
console.log(x); // logs "undefined"
console.log(y); // throws ReferenceError exception
```

# 3. Dynamic Type (동적 타입)

C-family language은 변수를 선언할 때 미리 data type(자료형)을 정하고 data type에 맞는 값을 대입(할당)하여야한다. (statically typed languages)

```c
int main(void) {
  int num = 46;
  char * str = "String";

  num = "String"; // warning: incompatible pointer to integer conversion assigning to 'int' from 'char [7]'

  return 0;
}
```

Javascript는 동적 타입(dynamic typed) 언어 혹은 느슨한 타입(loosely typed) 언어이다. 이것은 변수의 data type을 미리 선언할 필요없이 값이 할당되는 과정에서 자동으로 data type이 결정될 것이라는 뜻이다. 따라서 같은 변수에 여러 data type의 값을 대입할 수 있다.

```javascript
var foo;

console.log(typeof foo);  // undefined

foo = null;
console.log(typeof foo);  // object

foo = {};
console.log(typeof foo);  // object

foo = 3;
console.log(typeof foo);  // number
foo = 3.14;
console.log(typeof foo);  // number

foo = "Hi there";            
console.log(typeof foo);  // string

foo = true;                  
console.log(typeof foo);  // boolean
```

# 4. Pass-by-value

```javascript
// Pass-by-value
var a = 1;
var b = a;

console.log(a, b);    // 1  1
console.log(a === b); // true

a = 10;
console.log(a, b);    // 1  10
console.log(a === b); // false
```

변수 a는 기본료형인 number type의 1을 저장하고 있다. 기본자료형의 경우 값이 복사되어 변수에 저장된다. 즉 참조형으로 저장되는 것이 아니라 값 자체가 저장되게 된다. 변수 b에 변수 a를 대입할 경우, 변수 a의 값 1은 복사되어 변수 b에 저장된다.

# 5. Immutability in JavaScript

Immutability (변경불가성)은 함수형 프로그래밍의 핵심 원리이다. 뿐만 아니라, 객체 지향 프로그램을 위한 기능을 제공하고 있다

`object` type을 제외한 모든 data type은 한번 정해지면 변경이 불가능한 값 (immutable value)이다.
C 언어와는 다르게도, 문자열은 변경 불가능한 값 (immutable) 이다. 이런 값을 "primitive values" 라 한다. 
(변경이 불가능하다는 뜻은 메모리 영역에서의 변경이 불가능하다는 뜻이다. 재할당은 가능하다)

```javascript
var statement = "I am an immutable value"; // String is an immutable value
var otherStr = statement.slice(8, 17);     // “immutable”
console.log(statement);                    
```

2행에서 Stirng 객체의 slice 메서드는 statement 변수에 저장된 문자열을 변경하는 것이 아니라 사실은 새로운 문자열을 생성하여 반환하고 있다. 그 이유는 문자열은 변경할 수 없는 immutable value이기 때문이다.

```javascript
var arr = [];
var v2 = arr.push(2);
```

상기 예제에서 v2의 값은 무엇인가? 문자열의 예와 같이 배열이 동작한다면 v2는 새로운 배열(하나의 요소를 가지고 그 값은 2인)을 가지게 될 것이다. 그러나 객체인 arr은 push 메서드에 의해 update되고 v2에는 배열의 새로운 `length` 값이 반환된다. ([Passing by Reference](http://ungmo2.github.io/javascript/Javascript-Object/#pass-by-reference) 참고)

# 6. Variable scope

Scope란 변수(매개변수 포함)에의 접근성과 생존기간(life-cycle)을 의미한다.

C-family language 대부분은 `block-scope`를 사용하지만 Javascript는 `function scope`를 사용한다.

```c
int main(void) {
  // block-scope
  if (1) {
    int x = 5;
    printf("x = %d\n", x);
  }

  printf("x = %d\n", x); // use of undeclared identifier 'x'

  return 0;
}
```

변수를 함수 밖에서 선언하면 `전역변수(Global variable)`가 된다. 전역변수는 어느 곳에서든지 접근이 가능하다.

함수 내부에서 선언된 변수는 함수 내부에서만 접근이 가능하다. 이런 변수를 `지역변수(Local variable)`이라한다.

```javascript
// non-block-scope
if (true) {
  var x = 5;
}
console.log(x);
```

```javascript
// Function-scope
var x = 1; // global variable

function foo() {
  x = 2;
  y = 3;  // 암묵적 전역
  var z = 4;  // local variable
}

foo();

console.log(x); // logs "2"
console.log(y); // logs "3"
console.log(z); // Throws a ReferenceError
```