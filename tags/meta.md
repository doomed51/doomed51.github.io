---
layout: tag_archive
title: "meta"
tag: meta
tag_name: meta
permalink: /tags/meta/
---

<h2>meta</h2>
<ul class="post-list">
  {% for post in site.tags[meta] %}
    <li>
      <span class="post-meta">{{ post.date | date: "%b %-d, %Y" }}</span>
      <h2>
        <a class="post-link" href="{{ post.url | relative_url }}">{{ post.title }}</a>
      </h2>
      {% if post.description %}
        <p>{{ post.description }}</p>
      {% endif %}
    </li>
  {% endfor %}
</ul>