---
layout: page
title: "SNA"
permalink: /categories/sna/
---
<div style="text-align: center; margin-top: 20px; font-size: 15px; font-style: italic;">
    "Birds of a feather flock together, but it's the strength of their social network that keeps them soaring high"
</div>
<hr style="margin-top: 20px; margin-bottom: 20px;">
<ul>
  {% for post in site.categories.SNA %}
  <li><a href="{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>
