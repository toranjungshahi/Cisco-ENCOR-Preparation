---
layout: default
title: Notes
permalink: /notes/
---

# Notes

PPT notes and supporting slide decks summarizing concepts, topology diagrams, and key takeaways for each lab.

<ul>
{% for file in site.static_files %}
  {% if file.path contains '/notes/' %}
  <li><a href="{{ site.baseurl }}{{ file.path }}" target="_blank" rel="noopener">{{ file.basename }}{{ file.extname }}</a></li>
  {% endif %}
{% endfor %}
</ul>

[← Back to Home]({{ site.baseurl }}/)
