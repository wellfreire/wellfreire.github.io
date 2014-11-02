---
layout: page
title: Blog Posts
excerpt: "An archive of blog posts sorted by date."
<!-- image:
  feature: so-simple-sample-image-4.jpg
  credit: WeGraphics
  creditlink: http://wegraphics.net/downloads/free-ultimate-blurred-background-pack/ -->
---

<ul class="post-list">
{% for post in site.posts %} 
  <li><article><a href="{{ site.url }}{{ post.url }}">{{ post.title }} <span class="entry-date"><time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%B %d, %Y" }}</time></span></a></article></li>
{% endfor %}
</ul>