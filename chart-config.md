---
layout: page
title: Chart config
permalink: /chart-config/
---

<div class="toc"></div>

## Format

Chart config is stored in a JSON object, broken down in to nested objects for 
the various components of the chart. The chart config can be stored in the 
[REST API](/rest-api), or used to generate interactive charts or images on the 
fly.

### Parameter types
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
      <td>Boolean</td>
      <td>i.e. true, false, 1, 0</td>
    </tr>
    <tr>
      <td>Color</td>
      <td>Accepts a hex, rgb or rgba string unless otherwise stated. i.e. #ffffff, rgb(255, 255, 255) or rgba(255, 255, 255, 0.5)</td>
    </tr>
  </tbody>
</table>

If a parameter type is followed by square brackets (i.e. Color[]) it implies you 
can send an array of that parameter type (e.g. ['#000000', '#ffffff'])

## Config object

{% for section_hash in site.data['chart-config'] %}
  {% assign sectionKey = section_hash[1]['key'] %}
  {% assign section = section_hash[1]['data'] %}
  {% include config/section.html sectionKey = sectionKey section = section %}
{% endfor %}