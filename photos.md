---
layout: page
---

{% for post in paginator.posts %}
{% for post in site.categories.photos %}

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
{% endfor %}

<div class="pagination">
  {% if paginator.next_page %}
    <a href="{{ paginator.next_page_path | prepend: site.baseurl }}">Older</a>
  {% else %}
    <!--<span>Older</span>-->
  {% endif %}
  {% if paginator.previous_page %}
    <a href="{{ paginator.previous_page_path | prepend: site.baseurl }}">Newer</a>
  {% else %}
    <!--<span>Newer</span>-->
  {% endif %}
</div>
