---
layout: default
title: Blog
permalink: /blog/
---

<h1>Blog posts</h1>

<!--
<div id="search-container">
<input type="text" id="search-input" placeholder="search...">
<ul id="results-container"></ul>
</div>

<script src="{{ site.baseurl }}/js/search-script.js" type="text/javascript"></script>

<script>
SimpleJekyllSearch({
  searchInput: document.getElementById('search-input'),
  resultsContainer: document.getElementById('results-container'),
  json: '{{ site.baseurl }}/search.json'
})
</script>
-->

<ul>
{% for p in site.posts %}
  <li><a href="{{ p.url }}">{{p.date | date: "%Y-%m-%d"}} - <span class="post-title">{{ p.title }}</span></a>
  {{p.excerpt}} [...] </li>
{% endfor %}
</ul>
