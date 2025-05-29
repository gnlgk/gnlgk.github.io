---
layout: post
title: javaScript
date: 2025-01-01 14:00 +0900
description: 
image: ../assets/img/front.jpg
category: [JS,]
tags: JS
published: true
sitemap: true
---

# TypeScript

## 타입앨리어스(type Alias)

Interface - 클래스의 값들을 규정한 것  
Type - 객체에 값을 묶어서 잠깐씩 정리해서 쓰는 용도, 한번쓰는용도?

````typescript
// 타입 앨리어스
type Person = {
  name: string,
  age?: number
}

// 빈 객체를 Person 타입으로 지정
const person = {} as Person;
person.name = 'Lee';
person.age = 20;
person.address = 'Seoul'; // Error
````

인터페이스는 extends 또는 implements될 수 있지만 타입 앨리어스는 extends 또는 implements될 수 없다.

enum: 상징적인 값
union: 중 에서 하나 선택  
````typescript
type Str = 'Lee';

type Union = string | null;

type Name = 'Lee' | 'Kim';

type Num = 1 | 2 | 3 | 4 | 5;

type Obj = {a: 1} | {b: 2};

type Func = (() => string) | (() => void);

type Shape = Square | Rectangle | Circle;

type Tuple = [string, boolean];
const t: Tuple = ['', '']; // Error
````

## 제네릭(Generic)
타입을 지정하기 어려울때 그때그때 받는 값에 따라 처리하고싶을 때/ 찬반논란(쓰긴하는데 반대도 있음)

제네릭: 선언 시점이 아니라 생성 시점에 타입을 명시하여 하나의 타입만이 아닌 다양한 타입을 사용할 수 있도록 하는 기법. T는 제네릭을 선언할 때 관용적으로 사용되는 식별자로 타입 파라미터(Type parameter)라 한다

````typescript
class Queue<T> { // 값 받아옴
  protected data: Array<T> = [];
  push(item: T) {
    this.data.push(item);
  }
  pop(): T | undefined {
    return this.data.shift();
  }
}

// number 전용 Queue
const numberQueue = new Queue<number>();

numberQueue.push(0);
// numberQueue.push('1'); // 의도하지 않은 실수를 사전 검출 가능
numberQueue.push(+'1');   // 실수를 사전 인지하고 수정할 수 있다

// ?. => optional chaining
// https://www.typescriptlang.org/docs/handbook/release-notes/typescript-3-7.html#optional-chaining
console.log(numberQueue.pop().toFixed()); // 0
console.log(numberQueue.pop().toFixed()); // 1
console.log(numberQueue.pop()?.toFixed()); // undefined

// string 전용 Queue
const stringQueue = new Queue<string>();

stringQueue.push('Hello');
stringQueue.push('World');

console.log(stringQueue.pop()?.toUpperCase()); // HELLO
console.log(stringQueue.pop()?.toUpperCase()); // WORLD
console.log(stringQueue.pop()?.toUpperCase()); // undefined

// 커스텀 객체 전용 Queue
const myQueue = new Queue<{name: string, age: number}>();
myQueue.push({name: 'Lee', age: 10});
myQueue.push({name: 'Kim', age: 20});

console.log(myQueue.pop()); // { name: 'Lee', age: 10 }
console.log(myQueue.pop()); // { name: 'Kim', age: 20 }
console.log(myQueue.pop()); // undefined
````

## optional chaining => ?
?.은 ?.'앞’의 평가 대상이 undefined나 null이면 평가를 멈추고 undefined를 반환합니다.
앞에 값이 있으면 뒤에꺼 실행













인터페이스랑 타입앨리어스 차이
제네릭이 뭔지