---
layout: page
---
<p align="center">
  <a href="http://theonlysiteever.com/microblog/">what is this?</a>
  <br />
  &#x25c7;
</p>

{% assign sorted-posts = site.posts | where: "layout","briefly" %}
{% for posts in sorted-posts offset: 0 limit: 20 %}

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
   This page only shows the 20 most recent posts. The previous posts are lost to the sands of time... not really, but they are not available here.
</p>
