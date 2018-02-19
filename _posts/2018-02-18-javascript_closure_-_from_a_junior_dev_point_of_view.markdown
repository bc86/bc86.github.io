---
layout: post
title:      "Javascript Closure - from a Junior dev point of view"
date:       2018-02-19 01:30:16 +0000
permalink:  javascript_closure_-_from_a_junior_dev_point_of_view
---


![](https://media.giphy.com/media/YAPvpvkw57I76/giphy.gif)

What exactly is Javascript closure? What is it used for? Let's break this fundamental principle down and use it in our future code. In his blog series about mastering the [Javascript Interview](htthttps://medium.com/javascript-scene/master-the-javascript-interview-what-is-a-closure-b2f0d2152b36p://) Eric Elliot made this comment about closure questions.

> If you can’t answer this question, you’re a junior developer. I don’t care how long you’ve been coding.

Harsh? Absolutely! Motivating? It should be. So let's get to it. MDN describes a Javascript closure like this - 

> A closure is the combination of a function and the lexical environment within which that function was declared.

![](https://media.giphy.com/media/SDxzM5LAVq5Tq/giphy.gif)

*Is it just me or does it always seem like your more confused after reading MDN's description?*  I thought Javascript is Sexy's description really helped describe it.

> A closure is an inner function that has access to the outer (enclosing) function’s variables—scope chain.

![](https://media.giphy.com/media/xUySTD7evBn33BMq3K/giphy.gif)

Time for an example to better understand exactly what is going on. 

```javascript
// Let's keep it simple

let a = 'global variable';

function closureExample() {
    let b = 'outer function variable';
		
		function closureFunction() {
        let c = 'inner function variable';
				return a + ' ' + b + ' ' + c;
    }
    return closureFunction();
}
closureExample(); // 'global variable outer function variable inner function variable'
```

A closure has 3 scope chains -
1. it's own scope (variables defined between it's own curly brackets) - or - `let c` in the function above
2. variable declared inside the outer function - or - `let b` in the function above
3. global variables - or - `let a` global scope above

Closures are also very popular in creating private functions and used with the Modular JS design pattern. Let's take a look at a private function which is inside an outer function.

```javascript
function example() {
    let amount = 1000;
    function privateFunction(ind) {
        return amount += ind;
    }
    return {
        a: privateFunction(100),
        b: privateFunction(2000)
    }
}
example(); // { a: 1100, b: 3100 }
```

With this example `privateFunction(ind)` is considered a private function because it is not accessable to the outside world. Javascript Closures are a very important fundamental to grasp that will only come with experience and practice. But are a must if you want to expand your knowledge and be considered a legitimate developer. 

There are plenty of other examples where closures are used. For example with Classes and inheritance. But that's for another day. On to the next topic. Bye.

![](https://media.giphy.com/media/jUwpNzg9IcyrK/giphy.gif)
