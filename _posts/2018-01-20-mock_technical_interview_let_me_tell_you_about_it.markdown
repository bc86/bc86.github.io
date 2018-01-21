---
layout: post
title:      "Mock Technical Interview... Let me tell you about it! 😡😤"
date:       2018-01-21 01:40:22 +0000
permalink:  mock_technical_interview_let_me_tell_you_about_it
---


> You always pass failure on your way to success - Michael Rooney

If that statement is true then I'm on my way. I just took a Javascript Mock Technical Interview and figured I would use this blog post to discuss the experience and what I learned. 

Being my first technical interview ever I went into it very nervous with no idea what to expect. I was asked questions like, 'What JS frameworks have you heard of?', 'Have you ever worked with ES6?', 'Have you worked with Node.js?'. Then came the million dollar question - The code challenge!

![](https://media.giphy.com/media/1h32z1PKhqDrq/giphy.gif)  
![](https://media3.giphy.com/media/Hs3idAl46U06I/giphy.gif)  


*Write a function that takes a string as an argument and returns the number of occurrences of each unique word, ignoring case and punctuation.*

![](https://media.giphy.com/media/ph6ewybUlGbW8/giphy.gif)


**What!** Ok when you read it, it sounds simple. But in the moment I froze. Let's break this question down though and see what we can learn. Ok so first things first, it's easier to take that string and turn it into an array and then count the elements. I was givin the string 'Gabba gabba hey, gabba gabba hey!'.
So to get started I started with this code -  
```javascript
str = str.replace(/\W/g, ' ').toLowerCase().split(/\s+/g);
```  
which resulted with this array -  
```javascript
[ 'gabba', 'gabba', 'hey', 'gabba', 'gabba', 'hey', '' ]
```
We will get back to that empty space string element at the end of the array later. But for now, so I have an array with elements, what do I do with them? Here's where I began to fall apart. How do I begin to count them? 

The instructor said, "what about adding each unique word into an object?"💡  
Why didn't I think of that? Ok so how do we push each unique element into the object? Let's create a function and find out

```javascript
function uniqueWordCount(str) {
    let obj = {};  
    str = str.replace(/\W/g, ' ').toLowerCase().split(/\s+/g);
    for (let i = 0; i < str.length; i++) {
        if (!(str[i] in obj) {
            obj[str[i]] = 0;
        }
        obj[str[i]] += 1;
    }
    return obj;
}
```

So what's going on inside this function block? First let's create a new obj with `let obj = {}`, so we have something to push each unique word into. We reassign the `str` argument to an array to loop through. Then we use a for loop to iterate through the `str` variable. First we use an if statement to check if the word is already inside the `obj` and if not we add it. Once the element is added we then increment it's value with `obj[str[i]] += 1`. Finally once the for loop is complete we return the `obj` itself with the pushed elements. 

So as a result we return an object with - `{gabba: 4, hey: 2, '': 1}`  
Wait a minute. What's that empty element doing in there? Remember I said we would come back to this? We only want to return words themselves, not empty strings. So how do we accomplish this?

```javascript
str = str.replace(/\W/g, ' ').toLowerCase().trim().split(/\s+/g);
```

**BAM**. The JS function `trim()` removes the whitespace so now we just return - `{gabba: 4, hey: 2}`. That's it! Problem solved. 

So what did we learn? That technical interviews are nerve racking but also how data structures play a part in software development as a whole. In the next blog post we can break down data structures and see how to use them. 
