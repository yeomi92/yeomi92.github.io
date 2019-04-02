---
layout: post
title: "let,cont"
subtitle: "ES6"
date: 2018-11-02 10:45:13 -0400
background: "/img/posts/06.jpg"
category: "javascript"
---
## let, const
###  var 
+ hoisting 가능
+ 변수 중복 선언 가능
+ 재할당 가능
+ function-scoped

~~~javascript
console.log(x); // undefined
var x = 10;
var x = 20;
{ 
  console.log(x); //20 
  x = 30; 
}
console.log(x); //30
~~~
### let
+ hoisting 불가능
+ 변수 중복 선언 불가능
+ 재할당 가능
+ block-scoped

~~~javascript
console.log(x); // error: z is not defined 
let x = 10; 
let x = 20; // error 
{ 
  console.log(x); // error: z is not defined 
  let x = 20;
  console.log(x); // 20 
}
console.log(x); // 10
~~~
### const
+ hoisting 불가능
+ 변수 중복 선언 불가능
+ 재할당 불가능
+ block-scoped

~~~javascript
console.log(x); // error: x is not defined
const x = 10; 
const x = 20; // error 
{ 
   console.log(x); // 10 
   x = 20; // error 
} 
x = 20; //error
~~~

## 왜 let, const를 써야할까?
+ 변수 재선언 문제 방지
+ hoisting 문제 방지

##### * 예제 코드들은 에러 발생 후 진행되지 않지만 한번에 작성하기위해서 위처럼 작성했습니다.
