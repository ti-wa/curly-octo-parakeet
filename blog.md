---
layout: page
title: Aus dem Atelier
permalink: /blog/
---

<div class="blog-index">
  {% for post in site.posts %}
  <article class="blog-post-item">
    <div class="blog-post-date">
      <time datetime="{{ post.date | date_to_xmlschema }}">
        {{ post.date | date: "%d. %m. %Y" }}
      </time>
    </div>
    <div class="blog-post-content">
      <h2><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h2>
      <p>{{ post.excerpt | strip_html | truncatewords: 30 }}</p>
      <a href="{{ post.url | relative_url }}" class="read-more">Weiterlesen &rarr;</a>
    </div>
  </article>
  {% endfor %}
</div>
