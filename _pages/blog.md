---
layout: default
permalink: /blog/
title: blog
nav: true
nav_order: 1
---

{% include bear.liquid %}

<div class="post bear-blog">

{% assign blog_name_size = site.blog_name | size %}
{% if blog_name_size > 0 %}

<h1>{{ site.blog_name }}</h1>
{% endif %}

  <ul class="bear-list">
    {% for post in site.posts %}
      <li>
        <span class="date">{{ post.date | date: "%d %b %Y" }}</span>
        {% if post.redirect == blank %}
          <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
        {% elsif post.redirect contains '://' %}
          <a href="{{ post.redirect }}" target="_blank" rel="noopener">{{ post.title }}</a>
        {% else %}
          <a href="{{ post.redirect | relative_url }}">{{ post.title }}</a>
        {% endif %}
      </li>
    {% endfor %}
  </ul>

</div>
