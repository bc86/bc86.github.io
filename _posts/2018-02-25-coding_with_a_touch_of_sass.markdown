---
layout: post
title:      "Coding with a touch of Sass"
date:       2018-02-26 02:12:57 +0000
permalink:  coding_with_a_touch_of_sass
---

## Learning the Ropes

![](https://media.giphy.com/media/l0IymiszgmwwfB5K0/giphy.gif)

I guess it’s better to be late then to never arrive. Sass has been around for a long while now. I know theres a few different CSS preprocessors out there, Stylus, LESS and Sass. We will be focusing on Sass this blog post. We will start at the beginning of including sass and then it’s features.

CSS has been around since 1995. As great as CSS has been it still has it's limitations. This is where Sass can help fill in the gaps. Sass gives CSS the ability to include things like variables, nesting and mixins to name a few. You say "big deal is it that serious, I can still create web sites with just vanilla CSS"?

![](https://media.giphy.com/media/xUPGcvs1sD2EwRkHM4/giphy.gif)

To get started first we need to include Sass in our project. Like all things with code there is a few different ways to include Sass in our project. We can install using-
* The original Ruby Sass binary. Install with `gem install sass`
* A GUI app such as [CodeKit](https://codekitapp.com/), [Hammer](http://hammerformac.com/), [LiveReload](http://livereload.com/)
* Using Yarn or NPM -
    * `npm install sass-loader node-sass` or
    * `yarn add sass-loader node-sass` 

What's better? It depends on you. If you are comfortable with the terminal then use yarn or npm but if you prefer pretty then use one of the GUI's listed on the [Sass install page](https://sass-lang.com/install). 

If your like me you wondered what's the difference between a .sass file and a .scss file. Let me show you with an example.
Here is Sass's original syntax.
```sass
$primaryColor: #eeccff

body
  $primaryColor: #ccc

  background: $primaryColor

p
  color: $primaryColor
```
Now the more recent SCSS file.
```scss
$primaryColor: #eeccff;

body {
  $primaryColor: #ccc;

  background: $primaryColor;
}

p {
  color: $primaryColor;
}
```
 
 See the difference? The original syntax of sass removed the familiar brackets and didn't require the ending semi-colons. But folks didn't like that syntax, so the scss syntax brought back the familiar CSS brackets and semi-colons. Personally I kinda liked the sass syntax but that's besides the point. Let's get to the good stuff.
 
 ## Variables
 
 Sass brings variable assignment to CSS. Something CSS has never had before. If you have any familiarity with Javascript you know about variables. A simple way to store a value to use throughout your style sheet. At this point we will be working with scss syntax but a simple reminder just remove the brackets and semi-colons and you have sass syntax. Stealing from Sass page a variable can be declared like this - 
 ```scss
$font-stack:    Helvetica, sans-serif;
$primary-color: #333;

body {
  font: 100% $font-stack;
  color: $primary-color;
}
 ```
 Here's two variables. `$font-stack` and `$primary-color`. Sass variables are declared with a $ in front. So this code now will add to body selector - 
 ```scss
 body {
  font: 100% Helvetica, sans-serif;
  color: #333;
}
```
Sass also provides variable scope. Interesting! So for instance if you declare a variable within a selector, it is then scoped within that selector. For example - 
```scss
$primary-color: #333;

body {
  $primary-color: #000;
  background-color: $primary-color;
}

p {
  color: $primary-color;
}
```
So `body` background-color is now `#000` not `#333`, but `p` is still `#333`. Also interesting, sass allows setting a variable to global using `!global`. For instance, `$primaryColor: #ccc !global;` will now set the `$primaryColor` variable globally to `#ccc`. Be careful using the global flag because you could get unexpected variable results. 
```scss
$primaryColor: #eeccff;

body {
  $primaryColor: #ccc !global;
  background: $primaryColor;
}

p {
  color: $primaryColor;
}
```
Now instead of the `p` tag having a color of `#eeccff` it has `#ccc`. There's also the `!default` flag which allows us to make sure there is a default value for a variable in the event that one is not provided.

## Functions...
![](https://media.giphy.com/media/oOTTyHRHj0HYY/giphy.gif)
That's right Tom Hanks. Sass brings functions to CSS. Functions in Sass help programmers stick to the DRY -or- "don't repeat yourself" principle. Sass comes with built in functions that for instance will darken a color or convert a string to upper case. Here is a [full list](http://sass-lang.com/documentation/Sass/Script/Functions.html) of the included functions with Sass. If the included functions aren't enough you can also create your own.
```scss
@function function-name(@args) {
  @return value-to-be-returned;
}
```
Functions are code blocks that return a single value of any Sass data type.
* strings
* numbers
* colors
* boolean
* null
*  lists of values, separated by spaces or commas
*  maps from one value to another
*  functions references
To create a function just start with `@function` followed by the name of the function and include any needed arguments. Then use `@return` to return the needed value. 

## Mixins
Some describe Sass Mixins and functions as kissing cousins. Mixins are very similar to functions. A mixin lets you make groups of CSS declarations that you want to reuse throughout your site. Two great examples of this would be for vendor prefixes and break points for your pages. Using the example from [Sass site](https://sass-lang.com/guide)
```scss
@mixin border-radius($radius) {
  -webkit-border-radius: $radius;
  -moz-border-radius: $radius;
  -ms-border-radius: $radius;
  border-radius: $radius;
}

.box { @include border-radius(10px); }
```
We create a mixin using `@mixin` followed by the name of the mixin which in this case is border-radius. This makes calling vendor prefix's throughout your CSS much easier. 

There's so much more to Sass that I haven't even mentioned yet. Things like operators, nesting, function directives and much much more. This post is meant to just get your feet wet with Sass. There is so much information and tutorials out there for Sass. Hope this article helped. Keep improving and using all the amazing tools that are at our disposal. Until next time.

![](https://media.giphy.com/media/3ohfFl3H65mgrJEYZq/giphy.gif)
