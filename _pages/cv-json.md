---
layout: archive
title: "CV"
permalink: /cv/
author_profile: true
redirect_from:
  - /resume
  - /cv-json/
---

{% include base_path %}

<p>You can also find my <a href="{{ base_path }}/files/CV.pdf" target="_blank">CV</a> here.</p>

{% assign cv = site.data.cv %}

<div class="cv-container">
  {% for section in cv %}
    <div class="cv-section">
      <h2>{{ section.title }}</h2>
      
      {% if section.type == "map" %}
        <ul>
        {% for item in section.contents %}
          <li><strong>{{ item.name }}:</strong> {{ item.value }}</li>
        {% endfor %}
        </ul>
      {% endif %}
      
      {% if section.type == "time_table" %}
        <ul class="cv-list">
        {% for item in section.contents %}
          <li class="cv-item" style="margin-bottom: 1.5em;">
            <div class="cv-item-header" style="display: flex; justify-content: space-between; align-items: baseline;">
              <div class="cv-item-title"><strong>{{ item.title }}</strong></div>
              <div class="cv-item-date" style="font-style: italic;">{{ item.year }}</div>
            </div>
            <div class="cv-item-content">
              <div class="cv-item-subtitle" style="color: #666;">{{ item.institution }}</div>
              {% if item.description.size > 0 %}
                <ul style="margin-top: 0.5em;">
                {% for desc in item.description %}
                  <li>{{ desc }}</li>
                {% endfor %}
                </ul>
              {% endif %}
            </div>
          </li>
        {% endfor %}
        </ul>
      {% endif %}
      
      {% if section.type == "nested_list" %}
        <ul>
        {% for item in section.contents %}
          <li>
            <strong>{{ item.title }}</strong>
            {% if item.items.size > 0 %}
              <ul>
              {% for subitem in item.items %}
                <li>{{ subitem }}</li>
              {% endfor %}
              </ul>
            {% endif %}
          </li>
        {% endfor %}
        </ul>
      {% endif %}
    </div>
  {% endfor %}
</div>
