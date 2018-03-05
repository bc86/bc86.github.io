---
layout: post
title:      "The Beginnings of the Ruby Language"
date:       2018-03-05 02:31:11 +0000
permalink:  the_beginnings_of_the_ruby_language
---

This is meant to be a very simple explanation of the Ruby Language. Let's get right into it. Wiki describes it this way - 

> Ruby is a dynamic, reflective, object-oriented, general-purpose programming language. It was designed and developed in the mid-1990s by Yukihiro "Matz" Matsumoto in Japan.

### Variables

Ruby is great when it comes to declaring variables. You just write the name that you wonna give the variable. Ruby variable names are snake case. Variable can be any of Ruby data types -
* Boolean
* Symbol
* Number
* String
* Array
* Hash

```ruby
int = 1995
super_simple_name = 'simple Ruby example'
bool = true

# this is a class variable
@@class_variable = 'use this with classes'

# this is a constant - begin with upper case letter
Language = 'Ruby'

# this is a global variable but this is not recommended
$global_variable = 'bad idea'
```
Other examples of variables are Ranges, Psuedo-variables. We won't cover them here.

### if else statements
An if else statement is a state that checks to see if a condition is true. If the condition is true it runs that particular code block. If it is false then it moves on to the next if statement and so on until the final else statement if nothing previously returns true.

```ruby
int = 15

if int < 10
    puts 'less then 10'
elsif int > 100
    puts 'greater then 100'
else 
    puts 'greater then 10 and less then 100'
```
A simplier way to write an if else statement is using a ternary operator. Ternary operator uses a ? and : for it's assignments. 

```ruby
automobile = 'truck'

automobile == 'truck' ? puts 'nice truck' : puts 'need better ride'
```
Ternary works great for simple if else statements. But if you need to use else if then ternary is not the way to go.

This is a very quick blog post on two simple things about the Ruby language. I will be writing more blogs about Ruby and Javascript soon.
