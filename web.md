---
layout: page
title: "Web Dev"
permalink: /web/
---

# Web Projects I've Made
(Often with help from ChatGPT)
<!-- {% assign directory = 'web-projects' %}
{% for file in site.static_files %}
  {% if file.path contains directory %}
    - <a href="{{ file.path }}">{{ file.name }}</a>
  {% endif %}
{% endfor %} -->
{% for page in site.pages %}
  {% if page.path contains '/web-projects/' %}
     - <a href="{{ page.url }}">{{ page.title }}</a>
  {% endif %}
{% endfor %}

# Interesting Webdev Tools
- https://edwardtufte.github.io/tufte-css/