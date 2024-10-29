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
> Create [archives.html](https://github.com/doomed51/doomed51.github.io/blob/main/archives.html) in root folder 

> make sure post font matter has "tags: ... "

> (optional)create a [custom layout](https://github.com/doomed51/doomed51.github.io/blob/main/_layouts/post_custom.html) in _layouts 