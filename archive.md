---
layout: page
title: Archive
---

## All Entries

{% for post in site.posts %}
{% if post.external-url %}
  * {{ post.date | date_to_string }} &raquo; [ {{ post.title }} &#x2192;]({{ post.url }})
{% else %}
  * {{ post.date | date_to_string }} &raquo; [ {{ post.title }} ]({{ post.url }})
{% endif %}
{% endfor %}

## Just Posts

{% for post in site.categories.post %}
  * {{ post.date | date_to_string }} &raquo; [ {{ post.title }} ]({{ post.url }})
{% endfor %}

## Just Links

{% for post in site.categories.linked-list %}
{% if post.external-url %}
  * {{ post.date | date_to_string }} &raquo; [ {{ post.title }} &#x2192;]({{ post.url }})
{% else %}
  * {{ post.date | date_to_string }} &raquo; [ {{ post.title }} ]({{ post.url }})
{% endif %}

{% endfor %}

## Just Photos

{% for post in site.categories.photo %}
  * {{ post.date | date_to_string }} &raquo; [ {{ post.title }} ]({{ post.url }})
{% endfor %}

## Just Briefly

{% for post in site.categories.briefly %}
  * {{ post.date | date_to_string }} &raquo; [ {{ post.title }} ]({{ post.url }})
{% endfor %}
