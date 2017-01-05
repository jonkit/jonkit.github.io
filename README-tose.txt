## Introduction

This file is created to hopefully prevent me from re-inventing the wheel every time I get the urge to create a blog. Rather than spending time starting from scratch, I am hoping that with a well-defined set of rules and clear outline, I can pick-up this iteration of the blog and just start writing.  

## Categories

There are four categories:  

+ post  
+ linked-list  
+ photo  
+ briefly  

Both `post` and `linked-list` appear in the main feed whereas `photo` and `briefly` have their own page and are available on Archive page.  

post - traditional blog posts, original content
linked-list - Daring Fireball-esque snippets and brief comment(s) linking to other content 
photo - my own private Instagram, hopefully providing me a reason to take and edit more photos
briefly - my attempt at one-off quips and random thoughts 

Any change to categories will impact the following files:  

+ archive.md 
+ index.html 
+ photos.md 
+ briefly.md 
+ any file in the /post folder 
+ atom.xml (all RSS feed files)

## Structure

### TOC

+ main page is a blog-roll with just `post` and `linked-list` items
+ `photo` and `briefly` items get their own blog-roll pages
+ archive page with a listing of all content as well as sections for each of the categories
+ about page with basic information about the site

### RSS Feeds

+ feed for just the main page (`post` and `linked-list`) where `linked-list` items point to the source
+ feed for just the main page (`post` and `linked-list`) where `linked-list` items point back this website
+ feed for just the photos  
+ feed for just the briefly snippets
+ feed for all content (`post`, `linked-list`, `photo`, and `briefly`) with all items pointing back to this website

Use HTML codes for characters to show up in the RSS feed (hex code elsewhere)

### Posts

+ file name to be YYYY-MM-DD-title-of-the-post.md (or YYYY-MM-DD-briefly-title-of-the-post.md for Briefly entries)
+ layout: use `post` for all entries except Briefly, which uses `briefly`
+ title: title the document as it would appear in the permalink on the main page
+ permalink: short-url-here is replaced with hyphenated text matching the post file name (without the date)
+ categories: specify which category the post will be associated with
+ external-url: only used for linked-list posts and entire line should removed for other posts
+ YAML Front Matter placeholder in Octopage.app is as follows:
---
layout: post briefly  
title: "Title"  
permalink: short-url-here  
categories: post linked-list photo briefly
external-url: removeifnolink
---
