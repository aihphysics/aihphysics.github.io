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
<!-- Display recipies without categories -->
  {%- assign sorted_recipies = site.recipies | sort: "importance" -%}
  <!-- Generate cards for each recipie -->
  <div class="grid">
    {%- for recipie in sorted_recipies -%}
      {% include recipies.html %}
    {%- endfor %}
  </div>
</div>
