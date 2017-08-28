---
layout: page
title: Archive
---

## Just Posts

{% for post in site.categories.post %}
<ul>
 <li>{{ post.date | date: "%m/%d/%y" }} &raquo; <a href="{{ post.url }}">{{ post.title }}</a></li>
</ul>
{% endfor %}

## Just Links

{% for post in site.categories.linked-list %}
<ul>
{% if post.external-url %}
 <li>{{ post.date | date: "%m/%d/%y" }} &raquo; <a href="{{ post.url }}">{{ post.title | truncate: 28 }} &#x2192;</a></li>
{% else %}
 <li>{{ post.date | date: "%m/%d/%y" }} &raquo; <a href="{{ post.url }}">{{ post.title }}</a></li>
{% endif %}
</ul>
{% endfor %}

## Just Photos

{% for post in site.categories.photos %}
<ul>
 <li>{{ post.date | date: "%m/%d/%y" }} &raquo; <a href="{{ post.url }}">{{ post.title }}</a></li>
</ul>
{% endfor %}
<!-- Also removing this because when used as a Twitter replacement it may fill up my Archive page quickly. All Briefly content will be on thr Briefly page. This is also the previous format that used Markdown lists instead of HTML  

## Just Briefly

{% for post in site.categories.briefly %}
  * {{ post.date | date_to_string }} &raquo; [ {{ post.title }} ]({{ post.url }})
{% endfor %}
-->
