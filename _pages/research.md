---
layout: research
title: "Research"
permalink: /research/
collection: research
author_profile: false
---

{% assign research_sorted = site.research | sort: "weight" %}

{% assign categories = "working:Working Papers|wip:Work in Progress|published:Publicationss" | split: "|" %}

{% for cat in categories %}
  {% assign pair = cat | split: ":" %}
  {% assign key = pair[0] %}
  {% assign label = pair[1] %}
  {% assign section = research_sorted | where: "category", key %}

  {% if section.size > 0 %}
  <h2 class="section-header">{{ label }}</h2>
  <div class="category-divider"></div>
  {% for post in section %}
    {% include archive-single.html %}
  {% endfor %}
  {% endif %}
{% endfor %}