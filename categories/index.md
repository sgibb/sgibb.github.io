---
title: Categories
layout: default
---

<ul>
{% for cat in site.categories %}
  <li id="{{ cat[0] }}" class="category">{{ cat[0] }}</li>
  {% for post in cat[1] %}
  <li>
    <time datetime="{{ post.date | date:"%Y-%m-%d" }}">{{ post.date | date:"%Y-%m-%d" }}</time>
    <a href="{{ post.url }}" title="{{ post.title }}">{{ post.title }}</a>
  </li>
  {% endfor %}
{% endfor %}
</ul>

