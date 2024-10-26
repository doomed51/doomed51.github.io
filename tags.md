---
layout: page
title: Browse by Tag
permalink: /tags/
---

# Browse Posts by Tag

Welcome to the tags page! Here you'll find all blog posts organized by their tags. Click on a tag to see all related posts.

{% raw %}
## Tag Cloud

{% include tag-cloud.html %}

## All Tags

{% assign tags_sorted = site.tags | sort %}
{% for tag in tags_sorted %}
  {% assign tag_slug = tag[0] %}
  {% assign posts = tag[1] %}
  {% assign tag_name = site.data.tags[tag_slug].name | default: tag_slug %}

### [{{ tag_name }}](#{{ tag_slug }}) ({{ posts.size }})

{% if site.data.tags[tag_slug].description %}
> {{ site.data.tags[tag_slug].description }}
{: .tag-description}
{% endif %}

{% for post in posts limit:5 %}
* [{{ post.title }}]({{ post.url }}) - {{ post.date | date: "%B %-d, %Y" }}
{% endfor %}

{% if posts.size > 5 %}
* [See all {{ posts.size }} posts tagged "{{ tag_name }}" →](/tags/{{ tag_slug }}/)
{: .more-link}
{% endif %}

{% endfor %}
{% endraw %}

<style>
.tag-description {
  color: #666;
  margin: 0.5rem 0 1rem;
  border-left-color: #ccc;
}

.more-link {
  list-style-type: none;
  margin-top: 1rem;
  font-style: italic;
}

h3 {
  border-bottom: 2px solid #eee;
  padding-bottom: 0.5rem;
  margin-top: 2rem;
}
</style>