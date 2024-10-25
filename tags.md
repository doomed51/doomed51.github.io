---
layout: page
title: Tags
permalink: /tags/
---

<div class="tag-cloud">
  {% assign tags = site.tags | sort %}
  {% for tag in tags %}
    <a href="{{ '/tags/' | append: tag[0] | slugify | relative_url }}" class="tag-link">
      {{ tag[0] }} ({{ tag[1].size }})
    </a>
  {% endfor %}
</div>

<style>
.tag-cloud {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
}

.tag-link {
  background: #f0f0f0;
  padding: 0.5rem 1rem;
  border-radius: 4px;
  text-decoration: none;
  color: #333;
}

.tag-link:hover {
  background: #e0e0e0;
}
</style>