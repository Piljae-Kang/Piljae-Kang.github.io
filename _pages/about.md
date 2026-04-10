---
permalink: /
title: "Piljae Kang"
author_profile: true
redirect_from: 
  - /about/
  - /about.html
---

{% include base_path %}

<div class="home-about__intro" markdown="0">
  {{ site.data.cv.basics.summary }}
</div>

<div class="home-section">
  <h2 class="home-section__title">news</h2>
  {% assign news_sorted = site.data.home.news | sort: "date" | reverse %}
  <div class="home-timeline">
    {% for item in news_sorted %}
    <div class="home-timeline__row">
      <div class="home-timeline__date">{{ item.date | date: "%b %d, %Y" }}</div>
      <div class="home-timeline__body">{{ item.icon }} {{ item.text }}</div>
    </div>
    {% endfor %}
  </div>
</div>

<div class="home-section">
  <h2 class="home-section__title">education</h2>
  <div class="home-timeline">
    {% for edu in site.data.cv.education %}
    <div class="home-timeline__row">
      <div class="home-timeline__date">
        {% assign sd = edu.startDate %}
        {% assign sd_parts = sd | split: "-" %}
        {% if sd_parts.size < 3 %}
          {% assign sd = sd | append: "-01" %}
        {% endif %}
        {% if edu.endDate == "Present" %}
          {{ sd | date: "%b %d, %Y" }} – Present
        {% else %}
          {% assign ed = edu.endDate %}
          {% assign ed_parts = ed | split: "-" %}
          {% if ed_parts.size < 3 %}
            {% assign ed = ed | append: "-01" %}
          {% endif %}
          {{ sd | date: "%b %d, %Y" }} – {{ ed | date: "%b %d, %Y" }}
        {% endif %}
      </div>
      <div class="home-timeline__body">
        <strong>{{ edu.studyType }}</strong> in {{ edu.area }}, {{ edu.institution }}.
      </div>
    </div>
    {% endfor %}
  </div>
</div>

{% if site.publications.size > 0 %}
<div class="home-section">
  <h2 class="home-section__title">publications</h2>
  {% include publications-teaser-list.html %}
  <p class="home-section__more"><a href="{{ base_path }}/publications/">All publications →</a></p>
</div>
{% endif %}
