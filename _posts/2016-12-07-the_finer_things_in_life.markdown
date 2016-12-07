---
layout: post
title:  "The Finer Things In Life"
date:   2016-12-07 11:55:46 -0500
---

This one took much longer then I'd like to admit. Sometimes it's the simple things that hang you up. I hate to say it, but that's what messed me up. But I powered on and finally finished it. I won't mention how long it took me. Little over a week. But that's neither here nor there.

## Gentleman's Drink
On to the app. The Finer Things is a simple app where you can go to review different scotches. Create an account and post your review. It's as simple as that. I kept it very simple just to show the basic structure using sinatra. Hopefully in the future I'll be able to make it presentable and give it a little character.

## So Why Did It Take So Long?
If I've learned anything from this, it's usually the small things that mess everything up. I remember specifically it happened about three times. This is the very simple but painful one I struggled through.

`<a href="/reviews/:id/edit">Edit Review</a>`

That evil code right there is what had me running in circles for so long. When I was framing out my html in my views folder I quickly wrote this code thinking that I would go back and change it when I got to that point. My memory did not serve me well. I completely forgot about it.

So as I stared at my code for days, looking back I realized that I was staring in the wrong section of code. Finally I gave in and asked help from a Learn Instructor. He helped me understand more the error I was getting and why I was getting it. So I used that information to look around that evil code I mentioned before.

`<a href="/reviews/<%=@scotch.slug%>/edit">Edit Review</a>`

Whallah! Now I was able to access my edit page perfectly. The other two were a blew that I was able to work through on my own.

## So What Did I Learn?
Well I mean besides always checking the minor details. It was great to take what I learned and apply it without someone holding my hand. From the controllers to seeding my database. But also identifying why methods arent working. It's great to see things that you code now work in a browser. It's time to keep going and on to the next project. It only gets more advanced from here.  Guess it's on to the next thing.




