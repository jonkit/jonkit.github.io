---
layout: page
---
<p align="center">
  <a href="http://theonlysiteever.com/microblog/">What is this?</a>
  <br />
  &#x25c7;
</p>

{% for post in site.categories.briefly %}

<article class="post">

{{ post.content }}

<a href="{{ site.baseurl }}{{ post.url }}">
    <time datetime="{{ post.date | date_to_xmlschema }}" class="post-date">{{ post.date | date_to_string }}</time>
</a>


</article>

{% endfor %}
