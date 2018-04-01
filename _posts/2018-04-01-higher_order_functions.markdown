---
layout: post
title:      "Higher Order Functions"
date:       2018-04-01 23:04:45 +0000
permalink:  higher_order_functions
---


The concept of a higher order function is actually simple. A higher order function takes a function as an argument, or returns a function. This returned function is called a callback. Callback functions work great with the response of a fetch request to a server. Other examples of higher order functions are `.map`, `.reduce` and `.filter` functions.

```javascript
function names(data) {
    return data.names;
}

fetch(webpage, {
}).then(response => response.json()).then(data => names(data))
```

```javascript 
const arr = [1,2,3,5,6,7,8];

let total = arr.reduce((a, b) => {
    return a + b;
})
```

This just shows two small examples of higher order functions and callbacks. This is a simple but powerful concept when it comes to programming and also functional programming.
