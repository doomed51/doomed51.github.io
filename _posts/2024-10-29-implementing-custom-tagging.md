---
layout: post_custom
title: "Enabling archives and tagging on github pages"
tags: [guide, reference]
author: Rachit 
---

When [deploying a blog on GitHub Pages](./2024-10-16-quick-personal-site.md) you might want to add archives so that visitors are able to get a quick overview on the topics and subjects covered. 

But GH Pages is limited to [the default dependencies](https://pages.github.com/versions/), which does not include jekyll-archives which solves this problem. The other alternative may be to build locally and deploy on GH but evidence seems light that this works - while being worth the effort. 

Something similar can be accomplished with some custom JS. 

Pre: 
- Deploying with [Github Pages](https://pages.github.com/)
- Building with [jekyll](https://github.com/jekyll/jekyll) 
- Styling with [jekyll-minima theme ](https://github.com/jekyll/minima)

Steps: 
> Create archives.html in root folder 
`
---
layout: post
title: Archives
---
<main class="container-ideal">
  <!-- Collect unique tags from all posts -->
  {%- assign unique_tags = "" | split: "" -%}
  {%- for post in site.posts -%}
    {%- for tag in post.tags -%}
      {%- unless unique_tags contains tag -%}
        {%- assign unique_tags = unique_tags | push: tag -%}
      {%- endunless -%}
    {%- endfor -%}
  {%- endfor -%}
  {%- assign unique_tags = unique_tags | sort -%}

  <!-- Filter form -->
  <form id="tag-form" method="get" action="">
    <label for="tag-filter">Filter by tag:</label>
    <select name="tag" id="tag-filter">
      <option value="">All</option>
      {%- for tag in unique_tags -%}
        <option value="{{ tag }}">{{ tag | capitalize }}</option>
      {%- endfor -%}
    </select>
  </form>

  <page-archives id="archives">
    {%- assign date = "" -%}
    {%- for post in site.posts -%}
      {%- assign currentdate = post.date | date: "%Y" -%}
      {%- if currentdate != date -%}
        {%- unless forloop.first -%}</table>{% endunless %}
        <table class="year-table" data-year='{{post.date | date: "%Y"}}'>
          <caption id='{{post.date | date: "%Y"}}'>{{ currentdate }}</caption>
          <thead>
            <tr>
              <th scope="col">Date</th>
              <th scope="col">Title</th>
              <th scope="col">Tags</th>
            </tr>
          </thead>
          {%- assign date = currentdate -%}
      {%- endif -%}
      <tr class="post-row" data-tags="{{ post.tags | join: ',' }}">
        <td><time datetime="{{ post.date | date: '%Y-%m-%d' }}">{{ post.date | date: '%b %d' }}</time></td>
        <td><a href="{{ site.baseurl | prepend: site.url }}{{ post.url }}">{{ post.title }}</a></td>
        <td>{{ post.tags | join: ', ' }}</td>
      </tr>
      {%- if forloop.last -%}</table>{%- endif -%}
    {%- endfor -%}
  </page-archives>

  <script>
    document.addEventListener('DOMContentLoaded', function() {
      // Get the tag from URL if present
      const urlParams = new URLSearchParams(window.location.search);
      const selectedTag = urlParams.get('tag');
      
      // Set the dropdown to the selected tag if present
      if (selectedTag) {
        document.getElementById('tag-filter').value = selectedTag;
        filterPosts(selectedTag);
      }

      // Add change event listener to the dropdown
      document.getElementById('tag-filter').addEventListener('change', function(e) {
        const selectedTag = e.target.value;
        filterPosts(selectedTag);
        
        // Update URL
        const newUrl = selectedTag 
          ? `${window.location.pathname}?tag=${selectedTag}`
          : window.location.pathname;
        history.pushState({}, '', newUrl);
      });

      function filterPosts(tag) {
        const rows = document.getElementsByClassName('post-row');
        let visibleYears = new Set();

        // Show/hide rows based on tag
        Array.from(rows).forEach(row => {
          const postTags = row.dataset.tags.split(',');
          const shouldShow = !tag || postTags.includes(tag);
          row.style.display = shouldShow ? '' : 'none';
          
          if (shouldShow) {
            const yearTable = row.closest('.year-table');
            if (yearTable) {
              visibleYears.add(yearTable.dataset.year);
            }
          }
        });

        // Show/hide year tables based on whether they have visible posts
        const yearTables = document.getElementsByClassName('year-table');
        Array.from(yearTables).forEach(table => {
          table.style.display = visibleYears.has(table.dataset.year) ? '' : 'none';
        });
      }
    });
  </script>
</main>
`

> make sure post font matter has "tags: ... "

> (optional)create a custom layout in _layouts

`
<article class="post">
    {{ content }}
    {% if page.tags.size > 0 %}
    <div class="post-tags">
        <h5>Tags:</h5>
        {% for tag in page.tags %}
        {% assign tag_slug = tag %}
        {% assign tag_name = tag_slug %}
        <a href="/archives.html?tag={{ tag_slug }}" class="post-tag">
            {{ tag_name }}
        </a>
        {% endfor %}
    </div>
    {% endif %}
</article>
<style>
    .post-tags {
        margin-top: 0.5rem;
        padding-top: 1rem;
        border-top: 1px solid #eee;
    }

    .post-tag {
        display: inline-block;
        background: #0c0c0c;
        padding: 0.25rem 0.75rem;
        border-radius: 3px;
        margin-right: 0.5rem;
        margin-bottom: 0.5rem;
        text-decoration: none;
        color: #e2e0e0;
        font-size: 0.9rem;
    }

    .post-tag:hover {
        background: #837d7d;
        text-decoration: none;
    }
</style>
`

> 