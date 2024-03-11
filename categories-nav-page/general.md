---
layout: page
title: "General"
permalink: /categories/general/
---

<div style="text-align: center; margin-top: 20px; font-size: 15px; font-style: italic;">
    I need something here...
</div>

<hr style="margin-top: 20px; margin-bottom: 20px;">

<ul>
  {% for post in site.categories.general %}
  <li><a href="{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>
