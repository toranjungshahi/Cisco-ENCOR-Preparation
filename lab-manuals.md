---
layout: default
title: Lab Manuals
permalink: /lab-manuals/
---

# Lab Manuals

Browse all lab manuals below. Markdown manuals open as a themed page on this site; PDFs open in your browser's built-in PDF viewer.

## Manuals

<ul>
{% for page in site.pages %}
  {% if page.path contains 'Labs-Manuals/' and page.path contains '.md' %}
  <li><a href="{{ page.url | relative_url }}">{{ page.title | default: page.name }}</a></li>
  {% endif %}
{% endfor %}
</ul>

## PDF / Other Files

<ul>
{% for file in site.static_files %}
  {% if file.path contains '/Labs-Manuals/' %}
  <li><a href="{{ site.baseurl }}{{ file.path | uri_escape }}" target="_blank" rel="noopener">{{ file.basename }}</a></li>
  {% endif %}
{% endfor %}
</ul>

[← Back to Home]({{ site.baseurl }}/)
