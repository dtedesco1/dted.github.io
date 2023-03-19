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
    padding: 16px;
    border: 1px solid #ddd;
    border-radius: 4px;
    background-color: #f8f8f8;
    box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
    transition: box-shadow 0.3s;
  }

  .gallery-item:hover {
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  }

  .gallery-item a {
    display: block;
    margin-bottom: 8px;
    font-weight: bold;
    text-align: center;
    color: #333;
    text-decoration: none;
    transition: color 0.3s;
  }

  .gallery-item a:hover {
    color: #007bff;
  }

  .gallery-item iframe {
    width: 100%;
    border: 1px solid #ddd;
    box-shadow: 0 1px 3px rgba(0, 0, 0, 0.2);
  }
</style>

# Web Projects I've Made
(With help from ChatGPT)

# Web Projects I've Made
(Often with help from ChatGPT)

<div class="grid-gallery">
{% assign directory = 'web-projects' %}
{% for file in site.static_files %}
  {% if file.path contains directory %}
    <div class="gallery-item">
      <a href="{{ file.path }}" target="_blank" data-src="{{ file.path }}" data-filename="{{ file.name }}">Loading...</a>
      <iframe src="{{ file.path }}" width="200" height="150" frameborder="0"></iframe>
    </div>
  {% endif %}
{% endfor %}
</div>

<script>
  document.addEventListener('DOMContentLoaded', function () {
    const links = document.querySelectorAll('.gallery-item a[data-src]');

    links.forEach((link) => {
      const src = link.getAttribute('data-src');
      const filename = link.getAttribute('data-filename');

      fetch(src)
        .then((response) => response.text())
        .then((html) => {
          const parser = new DOMParser();
          const doc = parser.parseFromString(html, 'text/html');
          const title = doc.querySelector('title').innerText;
          link.innerText = title;
        })
        .catch((error) => {
          console.error('Error fetching HTML file:', error);
          link.innerText = filename; // Use the filename as the fallback
        });
    });
  });
</script>

# Interesting Webdev Tools
- https://edwardtufte.github.io/tufte-css/