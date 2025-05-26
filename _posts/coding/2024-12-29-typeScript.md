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

## 접근제한자

접근 제한자를 명시하지 않았을 때, 다른 클래스 기반 언어의 경우, 암묵적으로 protected(폴더)로 지정되어 패키지 레벨로 공개되지만 Typescript의 경우, 접근 제한자를 생략한 클래스 프로퍼티와 메소드는 암묵적으로 public이 선언된다.

접근 가능성	      public	protected	 private
클래스 내부	        ◯	       ◯	     ◯
자식 클래스 내부	  ◯	       ◯	      ✕
클래스 인스턴스	    ◯	       ✕	      ✕

````javascript
  constructor(public x: string) { }  // 생성자 파라미터에 선언가능, 자동 초기화
// - this.x가 자동선언됨
````

readonly :  readonly가 선언된 클래스 프로퍼티는 선언 시 또는 생성자 내부에서만 값을 할당할 수 있다. 그 외의 경우에는 값을 할당할 수 없고 오직 읽기만 가능한 상태가 된다. 이를 이용하여 상수의 선언에 사용한다. finally
````typescript
class Foo {
  private readonly MAX_LEN: number = 5; // 상수는 대문자로
  private readonly MSG: string;

  constructor() {
    this.MSG = 'hello';
  }

  log() {
    // readonly가 선언된 프로퍼티는 재할당이 금지된다.
    this.MAX_LEN = 10; // Cannot assign to 'MAX_LEN' because it is a constant or a read-only property.
    this.MSG = 'Hi'; // Cannot assign to 'MSG' because it is a constant or a read-only property.

    console.log(`MAX_LEN: ${this.MAX_LEN}`); // MAX_LEN: 5
    console.log(`MSG: ${this.MSG}`); // MSG: hello
  }
}
````

static : 정적 메소드는 클래스의 인스턴스가 아닌 클래스 이름으로 호출한다. static 키워드를 클래스 프로퍼티에도 사용할 수 있다. 
````typescript
class Foo {
  // 생성된 인스턴스의 갯수
  static instanceCounter = 0; // typescript에서는 속성도 static이 가능하다
  constructor() {
    // 생성자가 호출될 때마다 카운터를 1씩 증가시킨다.
    Foo.instanceCounter++;
  }
}

var foo1 = new Foo(); // static은 new의 대상이 아님
var foo2 = new Foo(); //  동일

console.log(Foo.instanceCounter);  // 2
console.log(foo2.instanceCounter); // error TS2339
````

abstract : 추상 메소드는 내용이 없이 메소드 이름과 타입만이 선언된 메소드를 말하며 추상 클래스를 상속한 클래스는 추상 클래스의 추상 메소드를 반드시 구현하여야 한다.

````typescript
abstract class Animal {
  // 추상 메소드
  abstract makeSound(): void;
  // 일반 메소드
  move(): void {
    console.log('roaming the earth...');
  }
}

// 직접 인스턴스를 생성할 수 없다.
// new Animal();
// error TS2511: Cannot create an instance of the abstract class 'Animal'.

class Dog extends Animal {
  // 추상 클래스를 상속한 클래스는 추상 클래스의 추상 메소드를 반드시 구현하여야 한다
  makeSound() {
    console.log('bowwow~~');
  }
}

const myDog = new Dog();
myDog.makeSound();
myDog.move();
````

