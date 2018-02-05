---
layout: post
title:      "Another `var`, `let` and `const` comparison"
date:       2018-02-05 04:28:36 +0000
permalink:  another_var_let_and_const_comparison
---


So I know I need a better way to start things off but... I got nothin. So let's just get going and see if we an learn anything. The grandfather of declaring a variable in Javascript was the good old `var` keyword. Using `var` you can assign any of the 7 data types in Javascript. But things get funky with `var`.  For instance this is perfectly valid code - 
```javascript
{
    console.log(badExample); // undefined
    var badExample = 3;
}
```

I don't know why you would wonna do that but you could. There are a bunch of examples of side effects from using the `var` keyword. This example shows variable hoisting, which returns `undefined` instead of a `ReferenceError: badExample is not defined`. A little confusing correct? So with ES6 it was time to fix this and along came `let` and `const` keywords. First up is the `let` keyword. Very similar to `var` except that now when assigning a value the variable's scope is considered block scope, not function scope or global if declared outside of a function. Here is same example but with `let` -
```javascript
{
    console.log(badExample); // ReferenceError: badExample is not defined
    let badExample = 3;
}
```

Way less confusing. From what i've seen and from reading other articles `let` is taking over `var` and is the preferred way of declaring variables. It's still ok to use `var` in for loops to assign initial value of counter but otherwise `let` is the preferred way.

There is still another keyword to consider. The `const` keyword is new with ES6 and is used to assign variable values. The `const` keyword is described as being used to assign values that won't change. `const` is block scope like `let`. But there are some gotchas to the reassigning. You can push to arrays assigned with `const`. For instance - 
```javascript
const numbers = [1, 2, 3, 4, 5]

numbers.push(6, 7, 8);

console.log(numbers); // [1, 2, 3, 4, 5, 6, 7, 8]
```

Interesting! That's just a simple example. There's so many things that hasn't been discussed in this article. I barely scratched the surface when considering these keywords. So get out there and start using ES6 and all the great features it brings with it. Till next time!
