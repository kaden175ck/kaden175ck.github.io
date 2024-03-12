---
layout: page
title: "Machine Learning"
permalink: /categories/machinelearning/
---
<div style="text-align: center; margin-top: 20px; font-size: 15px; font-style: italic;">
    Why did the computer go to art school? Because it wanted to learn machine learning!
</div>

<hr style="margin-top: 20px; margin-bottom: 20px;">
<ul>
  {% for post in site.categories.machine learning %}
  <li><a href="{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>
