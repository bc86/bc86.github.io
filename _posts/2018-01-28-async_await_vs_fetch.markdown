---
layout: post
title:      "async / await vs fetch"
date:       2018-01-29 02:26:17 +0000
permalink:  async_await_vs_fetch
---


Let's get right to it. First let's get some definitions out of the way.  

> The fetch() method of the WindowOrWorkerGlobalScope mixin starts the process of fetching a resource from the . network. This returns a promise that resolves to the Response object representing the response to your request.

Certainly not the clearest definition but we will get back to that. Next we have -  

> The async function declaration defines an asynchronous function, which returns an AsyncFunction object.

Ok not much better. Just one more to go - 

> The await operator is used to wait for a Promise. It can only be used inside an async function.

Why do docs definitions sometimes really make you more confused then you were before you looked these functions up?

Ok so basically all these functions have to do with is talking to API's and resources from networks. So let's use them already. First we'll use fetch.

```javascript
fetch('examplesite.com', {
    .......
}
.then(response => response.json())
.then(data => console.log(data)
```

Simple enough. Make a request, return a promise that we can resolve to a response object. Ok so next we combine await inside async like so.

```javascript
const request = async () => {
    const response = await fetch('examplesite.com');
    const json = await response.json();
    console.log(json)
}
request();
```

I kinda like it either way. But I guess to each there own. Using async though does increase performance. 
