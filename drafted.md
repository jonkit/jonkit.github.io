---
layout: page
---
<p align="center">
  Drafts or one-off things to share and then delete
  <br />
  &#x25c7;
</p>

{% if post.tags contains 'drafted' %}
<article class="post">

{{ post.content }}

<a href="{{ site.baseurl }}{{ post.url }}">
    <time datetime="{{ post.date | date_to_xmlschema }}" class="post-date">{{ post.date | date_to_string }}</time>
</a>


</article>

{% else %} 
  <!-- This is not a draft. Allow post to be displayed in blog lists and RSS feed --> 
{% endif %}
