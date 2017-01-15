---
layout: page
---

{% for post in site.categories.photo %}

  <article class="post">
    <!-- Changed this to H4 from H1 -->
    <h4 class="post-title">
      <a href="{{ site.baseurl }}{{ post.url }}">
        {{ post.title }} 
      </a>
    </h4>

    {{ post.content }}
    
    <time datetime="{{ post.date | date_to_xmlschema }}" class="post-date">{{ post.date | date_to_string }}</time>

    <!-- this is where the content was previous to the edit, it has been copied to show above the date
    {{ post.content }}
    -->
    
  </article>

{% endfor %}
