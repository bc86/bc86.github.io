---
layout: post
title:      "Component Lifecycle - `componentDidMount()` breakdown"
date:       2018-04-16 00:00:59 +0000
permalink:  component_lifecycle_-_componentdidmount_breakdown
---


React is a great JS library. Facebook has given us even more lifecycle methods with the release of React 16. But this blog post will take a minute and talk about a previous method. We will look at the `componentDidMount()` method and it's use cases.

React describes the `componentDidMount()` method as - `componentDidMount()` is invoked immediately after a component is mounted. So basically this is a great method to use to make a `fetch` request to a server to receive JSON. You might think that `componentWillMount()` would be better but no no this is not the case. React recommends `componentDidMount()` to make these requests.

Lets look at an example. So within my class component I call - 
```javascript
componentDidMount() {
    fetch(`${url}`, {
        method: 'GET',
        headers: `${included headers}`
		})
    .then(response => response.json())
    .then(data => {`${whatever your gonna do with the data}`}
    )
}			
```

`componentDidMount()` works great for these fetch calls to retrieve the data that will populate your page. Why create a new function that does this exact thing when React does it for us. Let's not reinvent the wheel people.

Well on to the next topic people. See you next time.

![](https://media.giphy.com/media/JDTsqJhvLOq9G/giphy.gif)
