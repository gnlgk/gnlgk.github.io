---
layout: post
title: javaScript
date: 2024-12-27 14:00 +0900
description: 
image: ../assets/img/front.jpg
category: [JS,]
tags: JS
published: true
sitemap: true
---

# 자바스크립트 기초   

## TypeScript

````javascript
let myV = 123;
myV = "ZARD"; // 데이터타입 변경 -> 동적타입(동적자료형)
// 정적타입(정적자료형) -> 같은 자료형을 담음
````

````typescript
function sum(a: number, b: number) { // 자료형 선언 방법 , default
  return a + b;
}

sum('x', 'y');
// error TS2345: Argument of type '"x"' is not assignable to parameter of type 'number'.
````

typescript 설치 및 버전 확인
vscode -> 인텔리센스(IntelliSense) -> $ npm install -g typescript -> tsc -v 

````typescript
class Person {
  private name: string; // 객체 밖에서 접근금지, 현재 클래스안에서만 사용가능, 형 선언

  constructor(name: string) { 
    this.name = name;
  }

  sayHello() {
    return "Hello, " + this.name;
  }
}

const person = new Person('Lee');

console.log(person.sayHello());
````

node 우선 설치
확장자는 .ts 
컴파일실행 tsc 파일명 -t ES2015
실행 node 파일명 (js로 컴파일 후 실행)

tsc --init // tsconfig.json -> "target": "es2015"로 변경

tsc --watch
tsconfig.json에 watch 옵션을 추가 가능
````json
{
  // ...
  "watch": true
}
````

vi -> vim -> neovim(nvim)

변수명 뒤에 데이터타입을 명시
````typescript
let foo: string = 'hello';
````

````typescript
// 함수선언식
function multiply1(x: number, y: number): number {
  //                                      ------ -> 함수의 return타입
  return x * y;
}
````

Type	      JS	 TS	    Description

boolean	    ◯	  ◯	    true와 false
null	      ◯	  ◯	    값이 없다는 것을 명시
undefined	  ◯	  ◯	    값을 할당하지 않은 변수의 초기값
number	    ◯	  ◯	    숫자(정수와 실수, Infinity, NaN) - 숫자에 Infinity, NaN 포함
string	    ◯	  ◯	    문자열
symbol	    ◯	  ◯	    고유하고 수정 불가능한 데이터 타입이며 주로 객체 프로퍼티들의 식별자로 사용(ES6에서 추가)
object	    ◯	  ◯	     객체형(참조형)
array	 	         ◯	    배열
tuple	 	         ◯	    고정된 요소수 만큼의 타입을 미리 선언후 배열을 표현
enum	 	         ◯	    열거형. 숫자값 집합에 이름을 지정한 것이다. // 상징적인 값
any	 	           ◯	    타입 추론(type inference)할 수 없거나 타입 체크가 필요없는 변수에 사용. var 키워드로 선언한 변수와 같이 어떤 타입의 값이라도 할당 가능.
void	       	   ◯	    일반적으로 함수에서 반환값이 없을 경우 사용한다.
never	 	         ◯	    결코 발생하지 않는 값

````typescript
// number
let decimal: number = 6;
let hex: number = 0xf00d;
let binary: number = 0b1010;
let octal: number = 0o744;
// 내부적으로 연산은 10진수로 처리함, toString()으로 진수가능

// array
let list1: any[] = [1, 'two', true]; // list를 사용할땐 any
let list2: number[] = [1, 2, 3]; // 일반적인 array
let list3: Array<number> = [1, 2, 3]; // 제네릭 배열 타입

// tuple : 고정된 요소수 만큼의 타입을 미리 선언후 배열을 표현
let tuple: [string, number]; // tuple: 형태를 직접 규정가능, 고정된 형태
tuple = ['hello', 10]; // OK
tuple = [10, 'hello']; // Error
tuple = ['hello', 10, 'world', 100]; // Error
tuple.push(true); // Error, 고정된 형태로 push 사용불가?

// enum : 열거형은 숫자값 집합에 이름을 지정한 것이다.
enum Color1 {Red, Green, Blue}; // 자동으로 숫자로 변경 c1가능 0, 1, 2
let c1: Color1 = Color1.Green;

console.log(c1); // 1

enum Color2 {Red = 1, Green, Blue}; // default값을 줘서 1, 2, 3
let c2: Color2 = Color2.Green;

console.log(c2); // 2

enum Color3 {Red = 1, Green = 2, Blue = 4};
let c3: Color3 = Color3.Blue;

console.log(c3); // 4

/*
any: 타입 추론(type inference)할 수 없거나 타입 체크가 필요 없는 변수에 사용한다.
var 키워드로 선언한 변수와 같이 어떤 타입의 값이라도 할당할 수 있다.
*/
let notSure: any = 4;
notSure = 'maybe a string instead';
notSure = false; // okay, definitely a boolean

// void : 일반적으로 함수에서 반환값이 없을 경우 사용한다.
function warnUser(): void { // return 값이 없음
  console.log("This is my warning message");
}

// never : 결코 발생하지 않는 값
function infiniteLoop(): never { // return 값이 절대 없음
  while (true) {}
}

function error(message: string): never {
  throw new Error(message);
}
````

typeScript가 기본 제공하는 타입은 모두 소문자
````typescript
// string: 원시 타입 문자열 타입
let primiteveStr: string;
primiteveStr = 'hello'; // OK
// 원시 타입 문자열 타입에 객체를 할당하였다.
primiteveStr = new String('hello'); // Error
/*
Type 'String' is not assignable to type 'string'.
'string' is a primitive, but 'String' is a wrapper object. Prefer using 'string' when possible.
*/

// String: String 생성자 함수로 생성된 String 래퍼 객체 타입
let objectStr: String;
objectStr = 'hello'; // OK
objectStr = new String('hello'); // OK
````

````typescript
// Date 타입
const today: Date = new Date();

// HTMLElement 타입
const elem: HTMLElement = document.getElementById('myId'); // HTMLElement를 꼭 써줘야 잡아올 수 있음

class Person { }
// Person 타입
const person: Person = new Person();
````

변수 타입이 여러개 일때
````typescript
let foo: string,   // 문자열 타입
    bar: number,   // 숫자 타입
    baz: boolean;  // 불리언 타입
````

casting - 강제 형변환  - cast(ing) : (n=1.23)실수 -> (n=1)정수처럼 작은값으로 이동, 그릇을 줄임, 문제발생
                      - Promotion : (n=1)정수 -> (n=1.24)실수처럼 큰값으로 이동, 그릇을 넓힘, 문제없음

Element(최상위) => HTMLElement, ... => HTMLDivElement, ...
Element 하위로 너무 많기때문에 HTMLElement를 사용하거나 그것보다 하위의 Element를 사용
````typescript
// as를 이용하여 HTMLInputElement 사용
const $input = document.querySelector('input["type="text"]') as HTMLInputElement;
const val = $input.value;
// 또는 타입 캐스팅을 위해 as 키워드 대신 <> 연산자를 사용할 수도 있다.
const $input = <HTMLInputElement>document.querySelector('input["type="text"]');
const val = $input.value;
````

https://poiemaweb.com/typescript-typing