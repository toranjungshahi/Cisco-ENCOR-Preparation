---
layout: default
title: Lab Packet Captures
permalink: /lab-pcap-files/
---

# Lab Packet Captures

Pcap files captured during labs, useful for visualizing protocol operation in Wireshark.

<ul>
{% for file in site.static_files %}
  {% if file.path contains '/lab-pcap-files/' %}
  <li><a href="{{ site.baseurl }}{{ file.path }}" target="_blank" rel="noopener">{{ file.basename }}{{ file.extname }}</a></li>
  {% endif %}
{% endfor %}
</ul>

[← Back to Home]({{ site.baseurl }}/)
