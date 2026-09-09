---
layout: default
title: Notes
permalink: /notes/
---

# Notes

PPT slide decks summarizing concepts, topology diagrams, and configurations from Cisco OCG book. Caution! Clicking below link will download them to your machine.

<ul>
{% for file in site.static_files %}
  {% if file.path contains '/Notes/' %}
  <li><a href="{{ site.baseurl }}{{ file.path | uri_escape }}" target="_blank" rel="noopener">{{ file.basename }}{{ file.extname }}</a></li>
  {% endif %}
{% endfor %}
</ul>

[← Back to Home]({{ site.baseurl }}/)
