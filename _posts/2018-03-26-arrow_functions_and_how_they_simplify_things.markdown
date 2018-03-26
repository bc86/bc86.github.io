---
layout: post
title:      "Arrow functions and how they simplify things"
date:       2018-03-26 04:58:21 +0000
permalink:  arrow_functions_and_how_they_simplify_things
---

When I first saw arrow functions my first thoughts were, “great something else for me to remember, but they sure look cool”. My thought process was a little ignorant at the time. Arrow functions serve a number of purposes. In this article I’ll touch on how it handles `this`, and in a follow up we will use them in a React component.

Arrow functions create a shorter syntax. Ok it doesn’t save a ton, but in my opinion it looks neater.

```javascript
// Without Arrow function
function double(int) {
    return int * 2;
}


// With Arrow function
let double = (int) => int * 2;
```

This is such a simple example. It doesn’t really represent the power of an arrow function. Don’t worry we will get to that just a little bit later.

Within Javascript you have to worry about a keyword called `this`. `this` normally refers to the object which owns the method but that also depends on how you call a function. `this` could represent global scope or an objects method for instance. An arrow function helps alleviate the need to use the `.bind` function because it doesn’t have it’s own `this`.

Arrow functions work great as callback functions to `fetch` responses. Let’s look at an example.

```javascript
fetch({}).then(response => response.json()).then(data => {whatever your gonna do with the data}
```

This is much easier then writing two different functions just to handle the response and it’s much more readable.
