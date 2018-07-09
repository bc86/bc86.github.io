---
layout: post
title:      "Ruby % String or % Notation what are they?"
date:       2018-07-09 01:13:05 +0000
permalink:  ruby_string_or_notation_what_are_they
---


![](https://media.giphy.com/media/tpdG5dt17HaO4/giphy.gif)

Let's look at a simple example to get things started. 

``` ruby
%(Here is a simple example of % notation)
=> "Here is a simple example of % notation"
```

All we did in this example was create a string with % notation. The syntax for this is pretty flexible. For instance we could of used -

``` ruby
%|This time I'm using pipes instead.|
=> "This time I'm using pipes instead."
```

As long as we use a non-alpha-numeric character for the delimiter we can really use anything. We could use -

``` ruby
%^Here is another example^
=> "Here is another example"
%ΩBut notice that we always have to have a closing delimiterΩ
=> "But notice that we always have to have a closing delimiter"
```

Something to keep in mind if we use `%(parentheses)` or `%{curly brackets}` or `%[square brackets]` or `%<pointy brackets>` as the delimiters we can use those same delimiters inside without escaping those characters. But the one catch is they must appear in balanced pairs. For example -

``` ruby
%[This will [work just] fine.]
=> "This will [work just] fine."

%{But this won't } work { correcty. }
SyntaxError: (irb):3: syntax error, unexpected tIDENTIFIER, expecting end-of-input
%{But this won't } work { correcty. }
```

Note to keep in mind. What if we wanted to return a parentheses without keeping the balanced pair structure? We would then need to escape that character. Like so -

``` ruby
%(We use the \ to escape a character like \).)
=> "We use the  to escape a character like )."
```

So is that it? Is that all we can do with % notation? No sir! There is plenty more. 

**Here's a list of common % strings:**
* %i - Array of Symbols
* %q - String
* %r - Regular Expression
* %s - Symbol
* %w - Array of Strings
* %x - Backtick (Capture Subshell Result)

Code examples are always better then just bullets.

``` ruby
kid = 'Isla'

%i(lets see what we get #{kid})
=> [:lets, :see, :what, :we, :get, :"\#{kid}"]
```

![](https://media.giphy.com/media/jWOLrt5JSNyXS/giphy.gif)

Wait that result shouldn't be that. Why when I tried to interpolate `kid` did it just return `:"\#{kid}"`? Let's try this - 

``` ruby
kid = 'Isla'

%I(lets see what we get now #{kid})
=> [:lets, :see, :what, :we, :get, :now, :Isla]
```

That is much better. I only changed one thing. I capitalized the i. With % notation if you want to interpolate you must use a capital letter instead of a lower case. Ok so `%i` or `%I` return an array of symbols. I'll just show examples of the rest now that we have interpolation out of the way.

``` ruby
kid = 'Isla'

%Q(#{kid} is the best baby.)
=> "Isla is the best baby."
# notice that %q and %Q return a string of the values

%r(#{kid})
=> /Isla/
# uh oh threw you a gotcha. Letters must be capitalized for interpolation except for %r. %r can use interpolation.

%s(father)
=> :father
# use this to create a single symbol whereas %i can be used to create an array of symbols

%W(#{kid} wife junior\ developer)
=> ["Isla", "wife", "junior developer"]
# notice I escaped the space so I could pass junior developer in as a single string

%x{ruby --copyright}
=> "ruby - Copyright (C) 1993-2016 Yukihiro Matsumoto\n"
```

I hope this sheds a little light on % notation. % notation is a great way to create String or Array literals. Well I think that's it for me for this blog post. so I guess until next time.

![](https://media.giphy.com/media/zmjKxrest6JBS/giphy.gif)
