---
layout: post
title: "Arrow Function과 this"
subtitle: "javascript"
date: 2020-10-04 -0400
background: "/img/posts/06.jpg"
category: "javascript"
---

arrow function은 lexical this를 가진다. 이는 상위 환경의 this를 계승받는 것이다.

es6

```
function Prefixer (prefix) {
    this.prefix = prefix
}
Prefixer.prototype.prefixArray = function (arr) {
    return arr.map(x => `${this.prefix} ${x}`)
}
const pre = new Prefixer('Hi')
console.log(pre.prefixArray(['Yeom', 'Cho']))
```

es5

```
function Prefixer (prefix) {
    this.prefix = prefix
}
Prefixer.prototype.prefixArray = function (arr) {
    console.log('out', this) // {prefix: 'Hi'}
    const self = this
	return arr.map(function (x) { 
        console.log('in', this); // Window
        return self.prefix + ' ' + x
    })
}
const pre = new Prefixer('Hi')
console.log(pre.prefixArray(['Yeom', 'Cho']))
```

#### arrow function를 사용하면 안되는 경우

#### 1\. 메소드

```
const person = {
    name: 'Yeom',
    sayHi: () => console.log(`Hi ${this.name}`) // this는 Window객체
}
person.sayHi() // Hi undefined
```

```
const person = {
    name: 'Yeom',
    sayHi: function () {
    	console.log(`Hi ${this.name}`) // this는 person
    }
}
person.sayHi() // Hi Yeom
```

#### 2\. prototype

```
const person = {
	name: 'Yeom'
}
person.prototype.sayHi = () => console.log(`Hi ${this.name}`)
person.sayHi() // Hi undefined
```

```
const person = {
	name: 'Yeom'
}
person.prototype.sayHi = function () {
    console.log(`Hi ${this.name}`) // this는 person
}
person.sayHi() // Hi Yeom
```

#### 3\. 생성자

생성자 함수에서 this는 새롭게 만들어진 객체를 가리킨다.

arrow function은 prototype속성 자체를 가지고 있지않다.

따라서 생성자 함수는 반드시 일반 함수로 정의해줘야한다.

```
const basic = function () { console.log('basic')}
basic.prototype // {constructor: ƒ}
let arrow = () => { console.log('arrow')}
arrow.prototype // undefined
```

#### 4\. addEventListener의 콜백 함수

arrow function을 addEventListener 함수의 콜백 함수로 정의하면 this는 전역 객체를 가리킨다.

```
const box = document.getElementById('box')
box.addEventListener('click', () => {
    console.log(this) // Window
})
```

```
const box = document.getElementById('box')
box.addEventListener('click', function () {
	console.log(this) // box
})
```