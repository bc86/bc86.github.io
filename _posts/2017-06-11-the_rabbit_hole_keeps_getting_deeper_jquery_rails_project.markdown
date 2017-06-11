---
layout: post
title:  "The Rabbit Hole keeps getting deeper!... jQuery / Rails Project"
date:   2017-06-11 22:47:19 +0000
---


I finally finished the jQuery front end portion of my rails project. I have learned a lot about the Javascript language during this project. I also learned even more about Ruby on Rails.  

Javascript is an interesting language that has many capabilities. However, depending on how it is implemented, could potentially crash and burn. Ok that is a little exaggerated. But when talking about class, constructors, and types of inheriting it can get very complicated. But that is for another blog post.  

I took a procedural approach to the project requirements. Things seemed to go relatively smooth. Initially I used jQuery's `.get()` and `.getJSON()` functions for my server requests. Then using jQuery to manipulate the DOM, added in the `get()` response. Wanting to incorporate a little more ES6 into my project I changed my `get()` requests with `fetch()` requests. But I was initially having trouble getting the requests to send properly. It just wasn't working. After banging my head against the wall and finally asking, I found out that my requests were missing the needed credentials property to send and receive correctly.  

Another problem I came across was how jquery and rails interact with each other. For a while I could not figure out why I needed to refresh my page for my javascript to work properly. At first, I thought I had something wrong with my javascript and how I implemented it. It wasn't until I noticed that if I typed my url in the search bar, then I did not have to refresh the page and javascript worked fine. Come to find out through searching and asking questions that rails and javascript don't exactly play nice together. For now I just removed turbolinks from require and my project. Maybe in the near future I'll add the `jquery-turbolinks` gem to help them get along. 

These are just two examples of road blocks I ran into while creating my project that really stood out to me. As I continue in my studies, I'm proud of how much I have learned. But it's humbling to realize how much I still don't know. With just the react project left in my studies I'm in the home stretch. I'm excited to complete this entire course.  

Also look out for future posts about specific language topics. Any suggestions you can email me at acodercalledcole@gmail.com.
