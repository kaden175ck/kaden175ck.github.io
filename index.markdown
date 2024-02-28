---
layout: default
---
<div style="text-align: center; margin-top: 20px; font-size: 24px; font-style: italic;">
    "The mountains are calling, and I must go."
</div>

<img src="/assets/images/mountains.webp" alt="Banner Image" style="width: 80%; height: auto; margin: 0 auto; display: block;"/>

<div>
    <h1>Categories</h1>
    <ul>
        <li><a href="/categories/sna">SNA</a></li>
        <li><a href="/categories/general">General</a></li>
        <li><a href="/categories/leetcode">LeetCode</a></li>
        <li><a href="/categories/machine learning">Machine Learning</a></li>
    </ul>
</div>

<div>
    <h2>Latest Posts</h2>
    <ul>
        {% for post in site.posts limit:3 %}
        <li>
            <a href="{{ post.url }}">{{ post.title }}</a>
            <p>{{ post.date | date: "%B %d, %Y" }}</p>
        </li>
        {% endfor %}
    </ul>
</div>
