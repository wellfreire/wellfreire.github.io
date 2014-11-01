---
layout: page
title: Posts por Categorias
excerpt: "An archive of posts sorted by category."
---

{% capture site_categories %}{% for category in site.categories %}{% unless category[0] == 'blog' %}{{ category | first }}{% unless forloop.last %},{% endunless %}{% endunless %}{% endfor %}{% endcapture %}
{% assign categories_list = site_categories | split:',' | sort %}

<ul class="tag-box inline">
  {% for item in (0..categories_list.size) %}{% unless forloop.last %}
    {% capture this_word %}{{ categories_list[item] | strip_newlines }}{% endcapture %}
    <li><a href="#{{ this_word }}">{{ this_word }} <span>{{ site.categories[this_word].size }}</span></a></li>
  {% endunless %}{% endfor %}
</ul>

{% for item in (0..site.categories.size) %}{% unless forloop.last %}
  {% capture this_word %}{{ categories_list[item] | strip_newlines }}{% endcapture %}
  <h2 id="{{ this_word }}">{{ this_word }}</h2>
  <ul class="post-list">
  {% for post in site.categories[this_word] %}{% if post.title != null %}
    <li><a href="{{ site.url }}{{ post.url }}">{{ post.title }}<span class="entry-date"><time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%B %d, %Y" }}</time></span></a></li>
  {% endif %}{% endfor %}
  </ul>
{% endunless %}{% endfor %}