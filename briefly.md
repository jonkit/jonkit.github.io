---
layout: page
title: Briefly
---

{% for post in site.categories.briefly %}

<article class="post">

<!-- removed title from the posts and made the permalink to the post by copying the <a href> from this section to the surround the date info
    <h1 class="post-title">
      <a href="{{ site.baseurl }}{{ post.url }}">
        {{ post.title }} 
      </a>
    </h1>
-->

{{ post.content }}

<a href="{{ site.baseurl }}{{ post.url }}">
    <time datetime="{{ post.date | date_to_xmlschema }}" class="post-date">{{ post.date | date_to_string }}</time>
</a>

<!-- this is where the content was previous to the edit, it has been copied to show above the date 
{{ post.content }}
-->    

</article>

{% endfor %}
