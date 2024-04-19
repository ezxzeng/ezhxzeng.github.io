---
layout: page
title: projects
permalink: /projects/
description: A growing collection of your cool projects.
nav: true
nav_order: 2
display_categories: all
horizontal: false
min_importance: 5
---
<!-- pages/projects.md -->
<div class="projects">
{%- if site.enable_project_categories and page.display_categories %}
  <!-- Display categorized projects -->
  {% if page.display_categories == "all" %}
    {% assign display_categories = site.projects | sort: "importance" | map: "category" | compact | uniq %}
  {% else %}
    {% assign display_categories = page.display_categories %}
  {% endif %}
  {%- for category in display_categories %}
  <h2 class="category">{{ category }}</h2>
  {%- assign categorized_projects = site.projects | where: "category", category -%}
  {%- assign sorted_projects = categorized_projects | sort: "importance" %}
  <!-- Generate cards for each project -->
  {% if page.horizontal -%}
  <div class="container">
    <div class="row row-cols-2">
    {%- for project in sorted_projects -%}
      {% if project.importance < page.min_importance %}
      {% include projects_horizontal.html %}
      {% endif %}
    {%- endfor %}
    </div>
  </div>
  {%- else -%}
  <div class="grid">
    {%- for project in sorted_projects -%}
      {% if project.importance < page.min_importance %}
      {% include projects.html %}
      {% endif %}
    {%- endfor %}
  </div>
  {%- endif -%}
  {% endfor %}

{%- else -%}
<!-- Display projects without categories -->
  {%- assign sorted_projects = site.projects | sort: "importance" -%}
  <!-- Generate cards for each project -->
  {% if page.horizontal -%}
  <div class="container">
    <div class="row row-cols-2">
    {%- for project in sorted_projects -%}
      {% if project.importance < page.min_importance %}
      {% include projects_horizontal.html %}
      {% endif %}
    {%- endfor %}
    </div>
  </div>
  {%- else -%}
  <div class="grid">
    {%- for project in sorted_projects -%}
      {% if project.importance < page.min_importance %}
      {% include projects.html %}
      {% endif %}
    {%- endfor %}
  </div>
  {%- endif -%}
{%- endif -%}
</div>
