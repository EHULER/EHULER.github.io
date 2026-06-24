---
layout: page
title: Bloga
permalink: /blog/
ref: blog
lang: es
---

<div class="wrapper">
  <h1>{{ page.title }}</h1>
  <p><a href="{{ '/eu/blog/feed.xml' | relative_url }}">RSS feeda</a></p>

  <ul class="post-list">
    {% assign es_posts = site.posts | where: "lang", "es" %}
    {% if es_posts.size > 0 %}
      {% for post in es_posts %}
        <li class="post-list-item">
          <article>
            <h2><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h2>
            <p class="post-meta">{{ post.date | date: "%-d %B %Y" }}</p>
            <p>{{ post.excerpt | strip_html | truncate: 200 }}</p>
          </article>
        </li>
      {% endfor %}
    {% else %}
      <p>No se han podido encontrar posts.</p>
    {% endif %}
  </ul>
</div>
