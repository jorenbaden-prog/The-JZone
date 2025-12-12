---
layout: splash
title: "Hey, I’m Joren"
tagline: "Authentic leadership driven by thoughtful creativity."
header:
  overlay_color: "#1a2a6c"    # soft white overlay
  overlay_filter: "0.55"      # light, milky transparency
  overlay_image: https://images.unsplash.com/photo-1520975922284-d2cb52271a8d?q=80&w=1200&auto=format&fit=crop

intro:
  - excerpt: "I share simple, useful ideas — so you leave happier than you arrived."
---

<h2 style="text-align: left;">You made it! Welcome to The JZone.</h2>
<p style="text-align: left; color: #666;"><em>Grab a coffee, look around, and learn something new.</em></p>

<h3 class="archive__subtitle" style="text-align: left; margin-top: 2em; border-bottom: 2px solid #0D132F; padding-bottom: 10px; display: inline-block;">Recent Work</h3>

<div class="grid__wrapper">
  {% assign recent_projects = site.projects | reverse %}
  {% for project in recent_projects limit:3 %}
    <div class="grid__item">
      <article class="archive__item" style="background: #f8f9fa; border-left: 5px solid #0D132F; padding: 20px; border-radius: 4px; box-shadow: 0 2px 4px rgba(0,0,0,0.1);">
        <h2 class="archive__item-title" itemprop="headline" style="margin-top: 0; font-size: 1.2em;">
          <a href="{{ project.url | relative_url }}" rel="permalink" style="color: #0D132F; text-decoration: none;">{{ project.title }}</a>
        </h2>
        {% if project.excerpt %}
          <div class="archive__item-excerpt" itemprop="description" style="font-size: 0.9em; margin-bottom: 15px;">
            <p>{{ project.excerpt | truncate: 120 }}</p>
          </div>
        {% endif %}
        <p style="margin-bottom: 0;"><a href="{{ project.url | relative_url }}" class="btn btn--primary" style="background-color: #0D132F; border-color: #0D132F;">View Project</a></p>
      </article>
    </div>
  {% endfor %}
</div>