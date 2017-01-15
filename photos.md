---
layout: page
---

{% for post in site.categories.photo %}

  <article class="post">
    <h3 class="post-title">
      <a href="{{ site.baseurl }}{{ post.url }}">
        {{ post.title }} 
      </a>
    </h3>

    <time datetime="{{ post.date | date_to_xmlschema }}" class="post-date">{{ post.date | date_to_string }}</time>

    {{ post.content }}
    
  </article>

{% endfor %}
