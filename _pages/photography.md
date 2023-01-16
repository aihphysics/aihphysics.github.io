---
layout: page
title: photography
permalink: /photography/
description: Just a few photos from my explorations. Let me know if you like them!
nav: true
nav_order: 3
display_categories: [ ]
horizontal: false
---

<!-- pages/photography.md -->
<div class="photography">
{%- if site.enable_project_categories and page.display_categories %}
  <!-- Display categorized photography -->
  {%- for category in page.display_categories %}
  <h2 class="category">{{ category }}</h2>
  {%- assign categorized_photography = site.photography | where: "category", category -%}
  {%- assign sorted_photography = categorized_photography | sort: "importance" %}
  <!-- Generate cards for each project -->
  {% if page.horizontal -%}
  <div class="container">
    <div class="row row-cols-2">
    {%- for project in sorted_photography -%}
      {% include photography_horizontal.html %}
    {%- endfor %}
    </div>
  </div>
  {%- else -%}
  <div class="grid">
    {%- for project in sorted_photography -%}
      {% include photography.html %}
    {%- endfor %}
  </div>
  {%- endif -%}
  {% endfor %}

{%- else -%}
<!-- Display photography without categories -->
  {%- assign sorted_photography = site.photography | sort: "importance" -%}
  <!-- Generate cards for each project -->
  {% if page.horizontal -%}
  <div class="container">
    <div class="row row-cols-2">
    {%- for project in sorted_photography -%}
      {% include photography_horizontal.html %}
    {%- endfor %}
    </div>
  </div>
  {%- else -%}
  <div class="grid">
    {%- for project in sorted_photography -%}
      {% include photography.html %}
    {%- endfor %}
  </div>
  {%- endif -%}
{%- endif -%}
</div>
