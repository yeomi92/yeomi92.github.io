---
layout: post
title: "Javascript의 this"
subtitle: "javascript"
date: 2020-10-04 -0400
background: "/img/posts/06.jpg"
category: "javascript"
---

### **javascript에서의 this의 4가지 문맥**

\- 함수 실행 : alert('Hello world!')

\- 메소드(함수 내부의) 실행 : console.log('Hello world!')

\- 생성자 실행 : new RegExp('\\\\d')

\- 간접(indirection) 실행 : alert.call(undefined, 'Hello world!');

#### 1\. 함수 실행

함수실행에서 this는 전역객체를 가리킨다.

```
function test () {
    console.log(this === window) // true
    console.log(this)
    // Window {parent: Window, opener: null, top: Window, length: 1, frames: Window, …}
}
console.log(this === window) // true
console.log(this)
// Window {parent: Window, opener: null, top: Window, length: 1, frames: Window, …}
```

#### 2\. 메소드 실행

메소드는 객체 내부의 속성, console.log()는 console객체의 log메소드 호출

메소드 실행에서 this는 메소드를 소유하고 있는 객체를 가리킨다.

```
const object = {
    test: function () {
        console.log(this === object) // true
    	console.log(this)
        // {test: ƒ}
    }
}
```

#### 3\. 생성자 실행

생성자 실행에서 this는 새롭게 만들어진 객체를 가리킨다.

```
function Test(name, num) {
    this.name = name
    this.num = num
}
Test.prototype.getName = function () {
    console.log(this === value) // true
    console.log(this)
    // Test {name: "test", num: 1}
	return this.name
}
const value = new Test('test', 1)
value.getName() // "test"
```

es6 문법 사용하여 생성자 실행

```
Class Test {
    constructor(name, num) {
    	this.name = name
        this.num = num
    }
    getName () {
    	return this.name
    }
}
Test.prototype.getName = function () {
    console.log(this === value) // true
    console.log(this)
    // Test {name: "test", num: 1}
	return this.name
}
const value = new Test('test', 1)
value.getName() // "test"
```

#### 4\. 간접 실행

간접실행은 함수가 메소드 호출로 실행되는 것을 말한다.

자바스크립트에서 함수는**일급객체**이다.

객체는 프로퍼티와 메소드를 가질 수 있다.

즉 함수도 프로퍼티와 메소드를 가질 수 있다.

공통으로 쓰이는 대표적은 프로퍼티는 length가 있고 메소드로는**call, apply, bind**등이 있다.

```
function increment (number) {
	return ++number
}
increment.call(undefined, 10) // 11
increment.apply(undefined, [10]) // 11
```

위는 increment함수가 call, apply메소드로 호출된 예시이다.

간접실행에서 this는 메소드의 첫번째 매개변수를 가리킨다.

```
const rabbit = { name: 'white rabbit' }
function concatName (string) {
	console.log(this === rabbit) // true
    return string + this.name
}
concatName.call(rabbit, 'Hello') // Hello white rabbit
concatName.apply(rabbit, ['Bye']) // Bye white rabbit
```

굳이 간접실행을 하는 이유는 무엇일까?

this의 활용에 답이 있다.

함수 실행에서 this의 문맥은 전역 객체였기때문에 this가 다른 객체를 가리키게하기 위해서는 간접실행을 활용한다.

#### 5\. Arrow Function

arrow function에서의 this는 arrow function이 정의된 곳의 문맥을 그대로 따른다.

arrow function에서의 this는 한번 bound되면 절대 바뀌지 않는 렉시컬 문맥을 따른다. this의 참조값이 결정되고나면 실행 문맥이 달라져도 변하지 않는다. 이를 lexical this라고 한다.

```
function objFunction () {
    console.log(this.foo) // 13 간접실행
    return {
    	foo: 25,
        bar: function () {
        	console.log(this.foo) // 25 메소드 실행
        }
    }
}
objFunction({foo: 13}).bar()
```

```
function objFunction () {
    console.log(this.foo) // 13 간접실행
    return {
    	foo: 25,
        bar: () => {
        	console.log(this.foo) // 13 간접실행할 때 this로 유지
        }
    }
}
objFunction.call({foo: 13}).bar()
```

arrow function은 실행도중 this의 스코프를 바꾸고 싶지않을 때 유용하다.