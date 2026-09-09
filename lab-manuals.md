---
layout: default
title: Lab Manuals
permalink: /lab-manuals/
---

# Lab Manuals

Browse all lab manuals below. Click a manual to open it in your browser's built-in PDF viewer.

<!-- TEMPORARY DEBUG: shows every static file Jekyll actually sees. Remove once the list above works. -->
<details>
<summary>Debug: all static files Jekyll found (click to expand)</summary>
<ul>
{% for file in site.static_files %}
  <li>{{ file.path }}</li>
{% endfor %}
</ul>
</details>

<ul>
{% for file in site.static_files %}
  {% if file.path contains '/lab-manuals/' %}
  <li><a href="{{ site.baseurl }}{{ file.path }}" target="_blank" rel="noopener">{{ file.basename }}</a></li>
  {% endif %}
{% endfor %}
</ul>

[← Back to Home]({{ site.baseurl }}/)
