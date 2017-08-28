---
layout: page
---

{% for post in site.categories.photos ofset: 0 limit: 10 %}

  <article class="post">
    <!--<h4 class="post-title" align="center">
      <a href="{{ site.baseurl }}{{ post.url }}">
        {{ post.title }}
      </a>
    </h4>-->

    <a href="{{ site.baseurl }}{{ post.url }}">
    <time datetime="{{ post.date | date_to_xmlschema }}" class="post-date">{{ post.date | date_to_string }}</time>
    </a>
    {{ post.content }}

  </article> 

{% endfor %}

<p align="center">
   &#x25c7;
   <br />
   This page only shows the 10 most recent photos. A full listing is on the <a href="http://theonlysiteever.com/archive/">Archive</a> page.
</p>
