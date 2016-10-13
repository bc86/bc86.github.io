---
layout: post
title:  "Time to Sink or Swim - The CLI Assessment Struggle"
date:   2016-10-13 04:22:17 +0000
---

As I opened the CLI assessment, I was overwhelmed with thoughts of, "Am I prepared for all of this"?  As I scrolled the page it seemed like more and more requirements appeared.  So where do I start?  I thought I knew, but I quickly found out how much I didn't know.

I don't need all those videos!  I'll just refer to them if I need to. WRONG!  I would have saved myself a lot of wasted time if I had checked out the videos first.  There is nothing worse then looking at other peoples gem files and wondering how they all came up with the same file structure.  What's wrong with me?!  Why doesn't my setup look like that?  First things first, use `bundle gem` to help create the files you need.  This made my life so much better.  Ok so what's next?  

Ok so I'm bundled, now let the scraping begin.  So the initial scraped site lists out the top ranked ski resorts of North America.  So far nothing earth shattering.  But then each of those resorts on that list link to their own webpage.  But now wait a minute for this to work I have to scrape a total of at least 30 pages.  I kept thinking I'm never going to get this to work.  Even if I do how am I going to correctly use that scraped information.  Google and anything else I can get my hands on, here I come.  

My initial thought process was to use two different methods.  One that would scrape the main page with it's list.  Then the second one I would make to scrape each of the individual pages that related to the resorts on the list.  Ok great I've got it all figured out.  Right?  Well I had my hypothesis all ready.  The only thing left now was to test it.  Frustrating long story short I couldn't get it to display correctly.  I was able to make the methods work individually but I failed bringing it all together.  On to the next hypothesis.  In a attempt to shorten my code but more importantly make it work correctly, I tried to combine those two methods into one.  But how can I scrape all those different pages with one single method?  With a couple `.map` uses, a little Regex and a hope and a dream.    
```
doc.search("tbody tr").map do |tbody_tr|
			hrefs = tbody_tr.search("td a").map { |a|
				a ['href'] if a['href'] =~ /^\/ski-resorts\// }.compact.uniq
				hrefs.each do |href|
					remote_url = BASE_ZRANKINGS_URL + href
```
That first line is straight forward enough.  That would be used to collect the list of resorts.  But after that is where things began to get a little more interesting.  This second `.map` is how I was able to collect each individual resorts link.  I found that each of the pages I needed to gain information from contained 'ski-resorts' within their link.  So using the Regex expression shown I was able to narrow down the resorts I collected.  Finally, I added an extension for each resort's page to the base url.  Success!  Now I was able to freely scrape any information I needed from the referenced pages.  

A huge sigh of relief is now deserved.  The only thing left to do is `gem build` and `gem push` my final product.  It feels great being able to post something that other people can use.  Thanks for reading guys.  Go check out my [gem](https://rubygems.org/gems/top_ranked_ski_resorts).  It's simple enough but it's the first of it's kind for me.  I'm proud of it.  Hopefully I can come back to it in near future and add on some features.
