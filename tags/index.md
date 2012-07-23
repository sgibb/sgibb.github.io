---
title: Categories
layout: default
---

<ul>
{% for tag in site.tags %}
  <li id="{{ tag[0] }}" class="tags">{{ tag[0] }}</li>
  {% for post in tag[1] %}
  <li>
    <time datetime="{{ post.date | date:"%Y-%m-%d" }}">{{ post.date | date:"%Y-%m-%d" }}</time>
    <a href="{{ post.url }}" title="{{ post.title }}">{{ post.title }}</a>
  </li>
  {% endfor %}
{% endfor %}
</ul>

