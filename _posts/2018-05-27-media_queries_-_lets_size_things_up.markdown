---
layout: post
title:      "Media Queries - Let's size things up"
date:       2018-05-28 01:30:09 +0000
permalink:  media_queries_-_lets_size_things_up
---

![](https://media.giphy.com/media/JBJ0wVpiY22Ag/giphy.gif)

Media queries have been around for a long while now. CSS v2 brought us Media types. But CSS v3 brought us Media Queries. These queries really give a developer or designer great control over their layout and design of their app or site.

Media Queries took Media types a step further. Instead of just checking for a type of media, say a screen, Media Queries check the capabilities of the device. This is great. It gives a developer the ability to say check the screen size and then based on the result serve say a certain image or page taylored to that result. With mobile search popularity booming it keeps a page from using unnecessary customer's data.

Here's a very very simple example in our CSS file.
``` css
div {
  background-color: green;
}

@media screen and (min-width: 500px) and (max-width: 899px) {
  div {
    background-color: red;
  }
}

@media screen and (min-width: 900px) and (max-width: 1000px) {
  div {
    background-color: blue;
  }
}
```

Ok so I removed all the other css from the file. Like centering and layout. This is just to represent how media queries work. So our first `div` sets the `background-color` to green. Then my first media query checks if the screen viewport size is at minimum 500px wide and not larger then 899px. If this is the case then the `background-color` is then set to red. The second media query checks the exact same thing except just with bigger viewport inputs.

I mentioned before about tayloring a site to not suck up unneccessary data. What did I mean by that. Well obviously it wasn't with changing `background-color`. What if we are dealing with images. Images can really suck up some data depending on how they are compressed or chosen and sized. Let's write a similar example but with images in mind.

``` css
div {
  background: url('small.jpg') no-repeat center center fixed;
  background-size: cover;
}

@media screen and (min-width: 500px) and (max-width: 899px) {
  div {
    background: url('medium.jpg') no-repeat center center fixed;
    background-size: cover;
  }
}

@media screen and (min-width: 900px) {
  div {
    background: url('large.jpg') no-repeat center center fixed;
    background-size: cover;
  }
}
```

So now based on the viewport size we will serve a corresponding image. Why does this matter?

![](https://media.giphy.com/media/wSCAy1zJbcUG4/giphy.gif)

This is where media queries really help control what is downloaded based on each device. In our previous code you might have noticed that we have three images. A small, medium and large.jpg. Each file is larger in memory size then the last. So if your user is using a mobile device then the small.jpg file will be downloaded, with neither of the other two files being downloaded. Which really helps critique design and performance.

![](https://media.giphy.com/media/6PdItpDwQ2CVG/giphy.gif)

Media queries though don't only check screen viewport size. This [overview](http://cssmediaqueries.com/overview.html) is a great resource for media queries. Also [CSS-tricks](https://css-tricks.com/css-media-queries/) has great example use cases.

Media query level 4 is still in production. But it looks like it's bringing some pretty cool features like, check if device has touch or hover capabilities to name a couple. 

Well that's it for this blog. So get out there and start catering your sites based on media queries. As for me I'm outer here till next time.

![](https://media.giphy.com/media/G5h04AkAvAHcs/giphy.gif)
