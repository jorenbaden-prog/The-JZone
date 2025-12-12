---
title: "Archives"
layout: single
permalink: /archives/
author_profile: false
classes: archives-nav
header:
  overlay_color: "#0D132F"
  overlay_filter: "0.5"
---

<div class="archive-filter" style="margin-bottom: 2em; padding: 1em; background: #f8f9fa; border-left: 5px solid #0D132F; border-radius: 4px;">
  <label for="category-filter" style="font-weight: bold; margin-right: 10px;">Filter by Category:</label>
  <select id="category-filter" onchange="filterPosts()" style="padding: 5px; border-radius: 4px; border: 1px solid #ccc;">
    <option value="all">Show All</option>
    {% assign categories = site.categories | sort %}
    {% for category in categories %}
      <option value="{{ category[0] | slugify }}">{{ category[0] | capitalize }}</option>
    {% endfor %}
  </select>
</div>

<div class="entries-list">
  {% for post in site.posts %}
    {% capture post_categories %}{% for category in post.categories %}{{ category | slugify }} {% endfor %}{% endcapture %}
    <article class="archive__item entry-item" data-categories="{{ post_categories | strip }}" style="margin-bottom: 2em; display: block;">
      <h2 class="archive__item-title" itemprop="headline">
        <a href="{{ post.url | relative_url }}" rel="permalink">{{ post.title }}</a>
      </h2>
      <div class="archive__item-teaser">
        <!-- <img src="{{ post.header.teaser | relative_url }}" alt=""> -->
      </div>
      <div class="archive__item-excerpt" itemprop="description">
        {{ post.excerpt | markdownify | truncate: 160 }}
      </div>
      <p style="font-size: 0.8em; color: #888;">
        <i class="fas fa-folder"></i> 
        {% for category in post.categories %}
          {{ category | capitalize }}{% unless forloop.last %}, {% endunless %}
        {% endfor %}
      </p>
    </article>
  {% endfor %}
</div>

<script>
function filterPosts() {
  var selector = document.getElementById('category-filter');
  var selectedCategory = selector.value;
  var entries = document.getElementsByClassName('entry-item');

  for (var i = 0; i < entries.length; i++) {
    var entry = entries[i];
    var categories = entry.getAttribute('data-categories').split(' ');

    if (selectedCategory === 'all' || categories.includes(selectedCategory)) {
      entry.style.display = 'block';
    } else {
      entry.style.display = 'none';
    }
  }
}
</script>
