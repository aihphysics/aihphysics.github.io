---
layout: page
title: recipies
permalink: /recipies/
description: I've been picking up recipies from a bunch of places and people for a while now, I hope you like them :)
nav: true
nav_order: 2
display_categories: [ programming hardware ]
horizontal: true
---

<!-- pages/recipies.md -->
<div class="recipies">
{%- if site.enable_project_categories and page.display_categories %}
  <!-- Display categorized recipies -->
  {%- for category in page.display_categories %}
  <h2 class="category">{{ category }}</h2>
  {%- assign categorized_recipies = site.recipies | where: "category", category -%}
  {%- assign sorted_recipies = categorized_recipies | sort: "importance" %}
  <!-- Generate cards for each project -->
  {% if page.horizontal -%}
  <div class="container">
    <div class="row row-cols-1">
    {%- for project in sorted_recipies -%}
      {% include recipies_horizontal.html %}
    {%- endfor %}
    </div>
  </div>
  {%- else -%}
  <div class="grid">
    {%- for project in sorted_recipies -%}
      {% include recipies.html %}
    {%- endfor %}
  </div>
  {%- endif -%}
  {% endfor %}

{%- else -%}
<!-- Display recipies without categories -->
  {%- assign sorted_recipies = site.recipies | sort: "importance" -%}
  <!-- Generate cards for each project -->
  {% if page.horizontal -%}
  <div class="container">
    <div class="row row-cols-1">
    {%- for project in sorted_recipies -%}
      {% include recipies_horizontal.html %}
    {%- endfor %}
    </div>
  </div>
  {%- else -%}
  <div class="grid">
    {%- for project in sorted_recipies -%}
      {% include recipies.html %}
    {%- endfor %}
  </div>
  {%- endif -%}
{%- endif -%}
</div>
