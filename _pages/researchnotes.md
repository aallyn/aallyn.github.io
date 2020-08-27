---
layout: page
title: research notes
permalink: /researchnotes/
description: A collection of research notes, mostly from reading papers and listening to talks.
nav: true
importance: 4
---

<div class="researchnotes grid">

  {% assign sorted_researchnotes = site.researchnotes | sort: "importance" %}
  {% for researchnote in sorted_researchnotes %}
  <div class="grid-item">
    {% if researchnote.redirect %}
    <a href="{{ researchnote.redirect }}" target="_blank">
    {% else %}
    <a href="{{ researchnote.url | relative_url }}">
    {% endif %}
      <div class="card hoverable">
        {% if researchnote.img %}
        <img src="{{ researchnote.img | relative_url }}" alt="researchnote thumbnail">
        {% endif %}
        <div class="card-body">
          <h2 class="card-title text-lowercase">{{ researchnote.title }}</h2>
          <p class="card-text">{{ researchnote.description }}</p>
          <div class="row ml-1 mr-1 p-0">
            {% if researchnote.github %}
            <div class="github-icon">
              <div class="icon" data-toggle="tooltip" title="Code Repository">
                <a href="{{ researchnote.github }}" target="_blank"><i class="fab fa-github gh-icon"></i></a>
              </div>
              {% if researchnote.github_stars %}
              <span class="stars" data-toggle="tooltip" title="GitHub Stars">
                <i class="fas fa-star"></i>
                <span id="{{ researchnote.github_stars }}-stars"></span>
              </span>
              {% endif %}
            </div>
            {% endif %}
          </div>
        </div>
      </div>
    </a>
  </div>
{% endfor %}

</div>
