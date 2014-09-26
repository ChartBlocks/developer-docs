---
layout: page
title: Chart config
permalink: /config/
---

## Table of contents
* [Parameter types](#parameter-types)
* [Config object](#config-object)
{% for section_hash in site.data.config %}
{% assign sectionKey = section_hash[0] %}
{% assign section = section_hash[1] %}
    * [{{ section.name }}](#config-{{sectionKey}})
{% endfor %}

## Paramter types
<table class="types">
  <tbody>
    <tr>
      <td>String</td>
      <td>Accepts a string, unless a set of valid values are specified.</td>
    </tr>
    <tr>
      <td>Integer</td>
      <td>i.e. 1, 4, 500</td>
    </tr>
    <tr>
      <td>Float</td>
      <td>i.e. 1, 1.0, 50.3</td>
    </tr>
    <tr>
      <td>Color</td>
      <td>Accepts a hex, rgb or rgba string unless otherwise stated. i.e. #ffffff, rgb(255, 255, 255) or rgba(255, 255, 255, 0.5)</td>
    </tr>
  </tbody>
</table>

## Config object

{% for section_hash in site.data.config %}
{% assign sectionKey = section_hash[0] %}
{% assign section = section_hash[1] %}
  {% include config/section.html %}
{% endfor %}