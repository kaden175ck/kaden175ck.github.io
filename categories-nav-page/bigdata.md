---
layout: page
title: "Big Data"
permalink: /categories/bigdata/
---

<div style="text-align: center; margin-top: 20px; font-size: 15px; font-style: italic;">
    Big data is big.
</div>

<hr style="margin-top: 20px; margin-bottom: 20px;">

<ul>
  {% for post in site.categories.bigdata %}
  <li><a href="{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>
