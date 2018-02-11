---
layout: post
title:      "What did we do before ES6 ?"
date:       2018-02-11 23:52:06 +0000
permalink:  what_did_we_do_before_es6
---

### Object.assign(), spread with a little rest

Those before us paved the way through the school of hard knocks.

![](https://media.giphy.com/media/119XrYvOgGgU0/giphy.gif)

Making things easier for those of us that may not of been coding when Javascript was called Livescript. Ok that's a little dramatic, but it is nice to see how Javascript has evolved and the simplicity that ES6 brings with it.

For instance with ES6 it brings `Object.assign()`, spread and rest with it. What are the benefits and drawbacks of each? Let's dig a little bit and see what we can find.

There's been a lot of hype around spread and rest but let's not forget about `Object.assign()`. MDN describes `Object.assign()` as -

> The Object.assign() method is used to copy the values of all enumerable own properties from one or more source objects to a target object. It will return the target object.

```javascript
const honda = { honda: {
  pilot: '3.5l',
  crv: '1.5t'
  }
};

const maserati = { maserati: {
  levante: 'v6tt',
  granTurismo: '4.7l'
  }
};

const finalCars = Object.assign({}, honda, maserati, { acura: { nsx: '3.5tt' } });

// finalCars = { pilot: '3.5l', crv: '1.5t', levante: 'v6tt', granTurismo: '4.7l', nsx: '3.5tt' };
```

This is simple enough. First we assign two objects `honda` and `maserati` to `finalCars` then we throw another object `acura` (notice a theme) at the time of assignment. Let's see the same example with the spread operator.

```javascript
const honda = { honda: {
  pilot: '3.5l',
  crv: '1.5t'
  }
};

const maserati = { maserati: {
  levante: 'v6tt',
  granTurismo: '4.7l'
  }
};

const finalCars = { ...honda, ...maserati, acura: { nsx: '3.5tt' }};

// finalCars = { pilot: '3.5l', crv: '1.5t', levante: 'v6tt', granTurismo: '4.7l', nsx: '3.5tt' };
```

Pretty straightward. A little less typing than using `Object.assign()`. MDN describes spread as - 

> allows an iterable such as an array expression or string to be expanded in places where zero or more arguments (for function calls) or elements (for array literals) are expected, or an object expression to be expanded in places where zero or more key-value pairs (for object literals) are expected.

Personally, I like the spread operator better. It's easier to read. `Object.assign()` is more verbose with what you can accomplish with returning objects. But a simple mistake like forgetting the empty `{}` as first parameter changes the created object. `Object.assign()` now references the given object instead of creating a new object. Example -

```javascript
const pontiac = { 
    gto: 'GTO'
}

let mitsubishi = Object.assign(pontiac);
console.log(mitsubishi === pontiac); // true

// That's not right. Pontiac isn't same manufacter as Mitsubishi
// Let's try this again but with {} braces

mitsubishi = Object.assign({}, pontiac);
console.log(mitsubishi === pontiac); // false
```

Pretty simple but important mistake. Spread operator doesn't have that problem. Although, for right now the spread operator has it's drawbacks right now. I believe currently it is waiting to officially be included in Javascript production. But with things like Babel it's to easy to not use. 

As this blog post is starting to run on let's quickly discuss the Javascript rest parameter. MDN describes it as - 

> rest parameter syntax allows us to represent an indefinite number of arguments as an array.

Now for an example. Couldn't relate this to cars off the top of my head so I'm just gonna work with what I got.

```javascript
function iGotNothing(...theArgs) {
    return theArgs.reduce((prev, next) => {
        return prev + next;
    })
}

iGotNothing(5, 6, 7, 8); // 26
```

Basically, what the rest parameter is doing is making it easy to include parameters inside a function. So now we can include as many parameters as necessary, without having to type them out individually. Let's look at one more example.

```javascript
function noDuplicates(...array) {
    return array.filter((a, b, arr) => {
        return arr.indexOf(a) === b;
    })
}

noDuplicates(2, 54, 100, 2, 54, 59, 2, 3); // [ 2, 54, 100, 59, 3 ]
```

Ok that wraps this blog post up. ES6 brings many benefits. Some that aren't quite finalized yet, but we can still use now because of things like Babel. Excited to see each new feature that comes down the pipeline. Please reach out at acodercalledcole@gmail.com with any constructive criticism. Until the next post.

![](https://media.giphy.com/media/QoesEe6tCbLyw/giphy.gif)

