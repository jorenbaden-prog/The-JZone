---
layout: single
title: "Archives"
permalink: /Archives/
---

<ul>
{% for post in site.posts %}
  <li>
    <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
    — {{ post.date | date: "%b %-d, %Y" }}
  </li>
{% endfor %}
</ul>
