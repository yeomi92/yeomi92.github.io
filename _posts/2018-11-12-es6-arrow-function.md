---
layout: post
title: "Arrow Function"
subtitle: "ES6"
date: 2018-11-12 10:45:13 -0400
background: "/img/posts/06.jpg"
---
## Arrow function
> 익명함수를 화살표 형태로 간략하게 쓸 수 있는 방법

### parameter가 없는 경우
~~~javascript
//ES5
function(){
  ...
}
        
//ES6
() => {...}
~~~

### parameter가 한 개인 경우
~~~javascript
//ES5
function(p1){
  ...
} 

//ES6
p1 => p1*p1 // return값이 없는 경우
p1 => {return p1*p1} // return값이 있는 경우
~~~

### parameter가 두 개 이상인 경우
~~~javascript
//ES5
function(p1,p2){
  ...
}

//ES6
(p1,p2) => p1*p2 //return값이 없는 경우
(p1,p2) => {return p1*p2} //return값이 있는 경우
~~~