---
layout: post
title:      "Not everybody has heard of the JS function `every`"
date:       2018-04-09 01:27:53 +0000
permalink:  not_everybody_has_heard_of_the_js_function_every
---

As we learn to program certain habits begin to develop in us. Is it our fault, no not necessarily. If your anything like me I've gotten pretty use to writing for loops with if else statements to test arrays. But wait! In certain circumstances you might decind to use a function called `every`. 

The `every()` method tests whether all elements in the array pass the test implemented by the provided function. Let's create a simple example to show `every` off. It will return `true` if all elements return `true`.

```javascript
const array = [1,2,3,4,5,6,7,8,9];

function checkIfBelow(arr) {
    return arr < 20;
}

console.log(array.every(checkIfBelow)); // true
```

That seems pretty simple right. If we did the same thing using a for loop it would look something like this.

```javascript
const array = [1,2,3,4,5,6,7,8,9];

function checkIfBelow(array) {
    for(let i = 0: i < array.length; i++) {
        array[i] < 20;
    }
}

console.log(checkIfBelow(array);
```

Alot less code huh. Now something I need to address. The for loop will check and output each individual element. So with that being said `every` is great when checking a bunch of elements if they return `true` to a certain requirement. `every` can also be great when working with the results of a `fetch` request. Like I always say there is so much to the Javascript that alot of times gets swept under the rug but offers great benefits. Well that is it for this post. Now it's on to the next.
