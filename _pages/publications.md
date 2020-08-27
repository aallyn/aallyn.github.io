---
layout: page
permalink: /publications/
title: publications
description: A collection of peer-reviewed publications
years: [2020, 2019, 2018, 2017, 2015, 2013, 2012, 2011]
nav: true
importance: 3
---

<div class="publications">

{% for y in page.years %}
  <h2 class="year">{{y}}</h2>
  {% bibliography -f papers -q @*[year={{y}}]* %}
{% endfor %}

</div>
