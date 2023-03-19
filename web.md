---
layout: page
title: "Web Dev"
permalink: /web/
---

<style>
  .grid-gallery {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    grid-gap: 16px;
    padding: 16px;
  }

  .gallery-item {
    position: relative;
    overflow: hidden;
  }

  .gallery-item a {
    display: block;
    margin-bottom: 8px;
    text-align: center;
  }

  .gallery-item iframe {
    width: 100%;
    border: 1px solid #ddd;
    box-shadow: 0 1px 3px rgba(0, 0, 0, 0.2);
  }
</style>

# Web Projects I've Made
(Often with help from ChatGPT)

<div class="grid-gallery">
{% assign directory = 'web-projects' %}
{% for file in site.static_files %}
  {% if file.path contains directory %}
    <div class="gallery-item">
      <a href="{{ file.path }}" target="_blank">{{ file.name }}</a>
      <iframe src="{{ file.path }}" width="200" height="150" frameborder="0"></iframe>
    </div>
  {% endif %}
{% endfor %}
</div>

# Interesting Webdev Tools
- https://edwardtufte.github.io/tufte-css/