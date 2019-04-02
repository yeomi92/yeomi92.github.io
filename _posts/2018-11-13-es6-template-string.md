---
layout: post
title: "Template String"
subtitle: "ES6"
date: 2018-11-13 10:45:13 -0400
background: "/img/posts/06.jpg"
---

## Template String
> ES6에 도입된 새로운 종류의 문자열 표기법.<br />
따옴표문자 `'`,`"` 가 아닌 백틱문자 <code>`</code>를 사용한다.

### ES5
~~~javascript
var x = 10;
var y = 20;
console.log('x값은 '+x+'이고 y값은'+y+'이다.');
~~~

### ES6
~~~javascript
let x = 10;
let y = 20;
console.log(`x값은 ${x}이고 y값은 ${y}이다.`);
~~~
