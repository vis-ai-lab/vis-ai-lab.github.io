---
layout: default
title: VisAI Lab | News
---

## News

<div class="news-list">
  {% assign news_items = site.news | where_exp: "item", "item.type != 'SERVICE'" | sort: 'date' | reverse %}
  {% for news in news_items %}
  {% include news-card.html %}
  {% endfor %}
</div>
