---
layout: page
---
<p align="center">
  <a href="http://theonlysiteever.com/microblog/">what is this?</a>
  <br />
  &#x25c7;
</p>

{% for post in site.categories.briefly offset: 0 limit: 10 %}

<article class="post">

{{ post.content }}

<a href="{{ site.baseurl }}{{ post.url }}">
    <time datetime="{{ post.date | date_to_xmlschema }}" class="post-date">{{ post.date | date_to_string }}</time>
</a>


</article>

{% endfor %}

<p align="center">
   &#x25c7;
   <br />
   This page only shows the 10 most recent posts. A full listing is on the <a href="http://theonlysiteever.com/archive/">Archive</a> page.
</p>
