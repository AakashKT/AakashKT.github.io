---
layout: page
permalink: /publications/
title: Publications
description: Full publications list.
years: [2023, 2022, 2021, 2019]
nav: true
nav_order: 2
---
<!-- _pages/publications.md -->
<div class="publications">

{%- for y in page.years %}
  <h2 class="">{{y}}</h2>
  <hr>
  {% bibliography -f papers -q @*[year={{y}}]* %}
  <br>
{% endfor %}

</div>
