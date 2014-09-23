---
layout: page
title: Chart config
permalink: /config/
---

We need to parse a lot of config here.

{% for section_hash in site.data.config %}
{% assign section = section_hash[1] %}
  <h2>{{ section.name }}</h2>
{% endfor %}