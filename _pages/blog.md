---
layout: default
permalink: /blog/
title: blog
nav: true
nav_order: 1
---

<style>
  .bear-blog {
    max-width: 42rem;
  }
  .bear-blog h1 {
    margin-bottom: 2rem;
  }
  .bear-list {
    list-style: none;
    padding: 0;
    margin: 0;
  }
  .bear-list li {
    display: flex;
    align-items: baseline;
    gap: 1rem;
    margin: 0.35rem 0;
  }
  .bear-list .date {
    flex: 0 0 auto;
    font-variant-numeric: tabular-nums;
    color: var(--global-text-color-light, #828282);
    font-size: 0.9rem;
    white-space: nowrap;
  }
  .bear-list a {
    text-decoration: none;
  }
  .bear-list a:hover {
    text-decoration: underline;
  }
</style>

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
