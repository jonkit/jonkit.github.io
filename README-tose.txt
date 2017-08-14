## Introduction

This file is created to hopefully prevent me from re-inventing the wheel every time I get the urge to create a blog. Rather than spending time starting from scratch, I am hoping that with a well-defined set of rules and clear outline, I can pick-up this iteration of the blog and just start writing.  

## Categories

There are four categories:  

+ post  
+ linked-list  
+ photos  
+ briefly  

Both `post` and `linked-list` appear in the main feed whereas `photos` and `briefly` have their own page and are available on Archive page.  

post - traditional blog posts, original content
linked-list - Daring Fireball-esque snippets and brief comment(s) linking to other content 
photos - my own private Instagram, hopefully providing me a reason to take and edit more photos
briefly - my attempt at one-off quips and random thoughts that are cross-posted to Micro.blog

Any change to categories will impact the following files:  

+ archive.md 
+ index.html 
+ photos.md 
+ briefly.md 
+ any file in the /post folder 
+ rss-FEEDNAME.xml (all RSS feed files)

## Structure

### TOC

+ main page is a blog-roll with just `post` and `linked-list` items
+ `photos` and `briefly` items get their own blog-roll pages
+ archive page with a listing of all content as well as sections for each of the categories
+ feed page listing all of the different RSS feeds
+ about page with basic information about the site

### RSS Feeds

+ feed for just the main page (`post` and `linked-list`) where `linked-list` items point to the source
+ feed for just the main page (`post` and `linked-list`) where `linked-list` items point back this website
+ feed for just the photos  
+ feed for just the photos that strips the title so it can be posted to Micro.blog
+ feed for just the briefly snippets
+ feed for all content (`post`, `linked-list`, `photo`, and `briefly`) with all items pointing back to this website

Use HTML codes for characters to show up in the RSS feed file (hex code elsewhere)

### Posts

+ file name to be YYYY-MM-DD-title-of-the-post.md 
    + append -briefly, -ll, and -photo between DD- and -title-of-post.md for sorting purposes
+ layout: use `post` for all entries except Briefly and Photos, which uses `briefly` and `photos`  
+ categories: specify which category the post will be associated with
+ hidden: value of `true` to be used for Briefly and Photos to hide them from the main feed pagination  
+ date: in the format YYYY-MM-DD HH:MM:SS and needs to have -0500 added after SS (with a space between)
+ permalink: short-url-here is replaced with hyphenated text matching the post file name (without the date)
+ title: title the post (matches permalink... except for linked-list where it is the linked post's title)  
+ external-url: only used for linked-list posts and entire line should removed for other posts

### YAML Front Matter Templates

+ Briefly Post  
---  
layout: briefly
category: briefly
hidden: true
date: YYYY-MM-DD HH:MM:SS -0500
permalink: name-of-md-file-without-date-or-extension
---

+ Photos Post  
---  
layout: photos
category: photos
hidden: true
date: YYYY-MM-DD HH:MM:SS -0500
permalink: name-of-md-file-without-date-or-extension
title: "Title of Post (Matches File Name But with Title Case)"
---

+ Standard Post
---  
layout: post  
category: post  
date: YYYY-MM-DD HH:MM:SS -0500
permalink: name-of-md-file-without-date-or-extension
title: "Title of Post (Matches File Name But with Title Case)"
---

+ Linked-list Post  
---  
layout: post
category: linked-list
date: YYYY-MM-DD HH:MM:SS -0500
permalink: name-of-md-file-without-date-or-extension
title: "Title of Post (Matches the Linked Article Title)"
external-url: urlbeinglinkedto
---

+ * NO LONGER USED * YAML Front Matter placeholder in Octopage.app is as follows:
---
layout: post briefly photos  
title: "Title"  
permalink: short-url-here  
categories: post linked-list photos briefly
external-url: removethiswholelineifnolink
---
