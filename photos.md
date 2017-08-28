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

