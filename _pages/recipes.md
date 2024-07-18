---
layout: page
title: recipes
permalink: /recipes/
description: I've been picking up recipes from a bunch of places and people for a while now, I hope you like them :)
nav: true
nav_order: 5
display_categories: [ programming hardware ]
horizontal: true
---

<!-- pages/recipes.md -->
<div class="recipes">
<!-- Display recipes without categories -->
  {%- assign sorted_recipes = site.recipes | sort: "importance" -%}
  <!-- Generate cards for each recipie -->
  <div class="grid">
    {%- for recipie in sorted_recipes -%}
      {% include recipes.html %}
    {%- endfor %}
  </div>
</div>
