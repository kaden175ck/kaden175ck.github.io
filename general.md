---
layout: page
title: "General"
permalink: /categories/general/
---

<h1>{{ page.title }}</h1>

<ul>
  {% for post in site.categories.general %}
  <li><a href="{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>
