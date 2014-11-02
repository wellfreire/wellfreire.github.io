---
layout: page
lang: en
title: All Posts
excerpt: "An archive of blog posts sorted by date."
<!-- image:
  feature: so-simple-sample-image-4.jpg
  credit: WeGraphics
  creditlink: http://wegraphics.net/downloads/free-ultimate-blurred-background-pack/ -->
---

{% assign posts = site.posts | where: "lang", page.lang %}

<ul class="post-list">
{% for post in posts %} 
  <li><article><a href="{{ site.url }}{{ post.url }}">{{ post.title }} <span class="entry-date"><time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%B %d, %Y" }}</time></span></a></article></li>
{% endfor %}
</ul>