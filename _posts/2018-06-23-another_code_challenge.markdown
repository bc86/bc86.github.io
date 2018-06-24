---
layout: post
title:      "Another Code Challenge"
date:       2018-06-24 03:02:31 +0000
permalink:  another_code_challenge
---


![](https://media.giphy.com/media/QHE5gWI0QjqF2/giphy.gif)

Let's get right into it. First let's address the Fibonacci sequence. For those of you that don't know the Fibonacci sequence is a sequence of numbers when the previous two added together equal the next one. For example, 1, 1, 2, 3, 5, 8, 13, 21, 34 and so on. Written as a rule, the expression is Xn = Xn-1 + Xn-2

Here's a a very basic example of coming up with the desired Fibonacci number. But we will address something afterward.

```javascript
function fibonacci(position) {
  if (position < 3) return 1;
  else return fibonacci(position - 1) + fibonacci(position - 2);
}

fibonacci(12)   //144
```

Pretty simple function right? But we have a problem with function. This function has terrible exponential time complexity. Finding the 12th position isn't to much of a demand. But when you jump up to let's say 100th or 1000th position then your in the take forever or crash your terminal time complexity. Let's create a new function that takes time complexity into consideration. This function is one I learned from a small simple Udemy course.

```javascript
function fibMemo(index, cache) {
  // index: index of number in fibonacci sequence
  // cache: an array used as memory
  cache = cache || [];
	if (cache[index]) return cache[index];
	else {
    if (index < 3) return 1;
	  else {
      cache[index] = fibMemo(index - 1, cache) + fibMemo(index - 2, cache)
      }
    }
  return cache[index];
}

fibMemo(1000) //4.346655768693743e+208
```

See what I mean? When I ran my first function with input of 100 my terminal locked up. Now with our new function I instead ran 1000 through and we received this value almost instantly. We can really see how Big-O notation plays a part in the efficiency of our functions. So as we code we always want to be thinking about this as we code so that our code doesn't get lazy and slow.

Well that's it for this blog. I'm outta here for now, until next time.

![](https://media.giphy.com/media/SbmB6uOeZLCX6/giphy.gif)


