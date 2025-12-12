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
  <label for="tag-filter" style="font-weight: bold; margin-right: 10px;">Filter by Topic:</label>
  <select id="tag-filter" onchange="filterPosts()" style="padding: 5px; border-radius: 4px; border: 1px solid #ccc;">
    <option value="all">Show All</option>
    {% assign tags = site.tags | sort %}
    {% for tag in tags %}
      <option value="{{ tag[0] | slugify }}">{{ tag[0] | capitalize }}</option>
    {% endfor %}
  </select>
</div>

<div class="entries-list">
  {% for post in site.posts %}
    {% capture post_tags %}{% for tag in post.tags %}{{ tag | slugify }} {% endfor %}{% endcapture %}
    <article class="archive__item entry-item" data-tags="{{ post_tags | strip }}" style="margin-bottom: 2em; display: block;">
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
        <i class="fas fa-tags"></i> 
        {% for tag in post.tags %}
          {{ tag | capitalize }}{% unless forloop.last %}, {% endunless %}
        {% endfor %}
      </p>
    </article>
  {% endfor %}
</div>

<script>
function filterPosts() {
  var selector = document.getElementById('tag-filter');
  var selectedTag = selector.value;
  var entries = document.getElementsByClassName('entry-item');

  for (var i = 0; i < entries.length; i++) {
    var entry = entries[i];
    var tags = entry.getAttribute('data-tags').split(' ');

    if (selectedTag === 'all' || tags.includes(selectedTag)) {
      entry.style.display = 'block';
    } else {
      entry.style.display = 'none';
    }
  }
}
</script>
