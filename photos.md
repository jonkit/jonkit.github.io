---
layout: page
---

{% for post in site.categories.photos %}

  <article class="post">
    <!-- Changed this to H4 from H1 -->
    <h4 class="post-title" align="center">
      <a href="{{ site.baseurl }}{{ post.url }}">
        {{ post.title }}
      </a>
    </h4>

    {{ post.content }}

    <time datetime="{{ post.date | date_to_xmlschema }}" class="post-date">{{ post.date | date_to_string }}</time>
   
  </article>

{% endfor %}
