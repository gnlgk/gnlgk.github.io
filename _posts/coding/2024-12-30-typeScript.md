---
layout: post
title: javaScript
date: 2024-12-29 14:00 +0900
description: 
image: ../assets/img/front.jpg
category: [JS,]
tags: JS
published: true
sitemap: true
---

# TypeScript

## Interface

- 인터페이스로 인스턴스를 통합관리, 객체로 봐도 무방하나 클래스는 아님
- 값을 넘기기전에 규정해서 인터페이스로 넘김, 규격을 만듬, 오고가는 값에 대한 규정
- new는 불가, 모든 메소드는 추상메소드
작은 의미: 값의 오고가는 형태를 만듬
큰 의미: 여러객체를 묶어 내가 필요한 값을 각 인스턴스에 전달

````typescript
// 인터페이스의 정의
interface Todo { // 값을 컨트롤하는 컨트롤러 역할 <= typeAlias가 더 어울림
  id: number;
  content: string;
  completed: boolean;
}

// 변수 todo의 타입으로 Todo 인터페이스를 선언하였다.
let todo: Todo;

// 변수 todo는 Todo 인터페이스를 준수하여야 한다.
todo = { id: 1, content: 'typescript', completed: false }; // 다른값은 추가 불가, 인터페이스 형에 맞춤, 애러X
````

````typescript
interface Todo { //<= typeAlias자리
  id: number;
  content: string;
  completed: boolean;
}

let todos: Todo[] = [];

// 파라미터 todo의 타입으로 Todo 인터페이스를 선언하였다.
function addTodo(todo: Todo) {
  todos = [...todos, todo];
}

// 파라미터 todo는 Todo 인터페이스를 준수하여야 한다.
const newTodo: Todo = { id: 1, content: 'typescript', completed: false };
addTodo(newTodo);
console.log(todos)
````

## 함수와 인터페이스

````typescript
interface SquareFunc {  // interface가 좀 더 어울림
  (num: number): number;
}

// 함수 인테페이스를 구현하는 함수는 인터페이스를 준수하여야 한다.
const squareFunc: SquareFunc = function (num: number) {
  return num * num;
}

console.log(squareFunc(10)); // 100
````

# 클래스와 인터페이스

- 인터페이스는 다중상속이 가능함
````typescript
interface ITodo {
  id: number;
  content: string;
  completed: boolean;
}

// Todo 클래스는 ITodo 인터페이스를 구현하여야 한다.
class Todo implements ITodo { // 생성자 안에는 인터페이스로 규정한 값이 들어와야됨
  constructor (
    public id: number,
    public content: string,
    public completed: boolean
  ) { }
}

const todo = new Todo(1, 'Typescript', false);

console.log(todo);
````

- 인터페이스는 프로퍼티뿐만 아니라 메소드도 포함할 수 있다. 단, 모든 메소드는 추상 메소드이어야 한다. 인터페이스를 구현하는 클래스는 인터페이스에서 정의한 프로퍼티와 추상 메소드를 반드시 구현하여야 한다.

## 덕 타이핑

````typescript
interface IDuck { // 1
  quack(): void;
}

class MallardDuck implements IDuck { // 3
  quack() {
    console.log('Quack!');
  }
}

class RedheadDuck { // 4
  quack() {
    console.log('q~uack!');
  }
}

function makeNoise(duck: IDuck): void { // 2
  duck.quack();
}

makeNoise(new MallardDuck()); // Quack!
makeNoise(new RedheadDuck()); // q~uack! // 5
````
- TypeScript는 해당 인터페이스에서 정의한 프로퍼티나 메소드를 가지고 있다면 그 인터페이스를 구현한 것으로 인정한다. 이것을 덕 타이핑(duck typing) 또는 구조적 타이핑(structural typing)이라 한다.


## 선택적 프로퍼티

````typescript
interface UserInfo {
  username: string;
  password: string;
  age?    : number;  // 선택적프로퍼티: 있어도되고 없어도되고
  address?: string;
}
````

## 인터페이스 상속

````typescript
interface Person {
  name: string;
  age?: number;
}

interface Developer {
  skills: string[];
}

interface WebDeveloper extends Person, Developer {
  grade: number; // 추가가능
} // extends 가능, 다중상속가능

const webDeveloper: WebDeveloper =  {
  name: 'Lee',
  age: 20,
  grade: 40,
  skills: ['HTML', 'CSS', 'JavaScript']
}
````


