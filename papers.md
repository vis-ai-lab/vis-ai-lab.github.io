---
layout: default
title: VisAI Lab | Papers
permalink: /papers/
---

<table class="publications">

{% assign by_year = site.publications | group_by: 'year' | sort: 'name' | reverse %}

{% for year_group in by_year %}
    <tr>
        <td colspan="2">
            <h3>{{ year_group.name }}</h3>
        </td>
    </tr>

    {% assign highlighted = "" | split: "" %}
    {% assign equal_contrib = "" | split: "" %}
    {% assign mentored = "" | split: "" %}
    {% assign others = "" | split: "" %}

    {% for pub in year_group.items %}
        {% assign first_author = pub.authors | first %}
        {% assign last_author = pub.authors | last %}
        {% if first_author contains "Sehi" or last_author contains "Sehi" %}
            {% assign highlighted = highlighted | push: pub %}
        {% elsif first_author contains "‡" %}
            {% assign equal_contrib = equal_contrib | push: pub %}
        {% elsif first_author contains "*" %}
            {% assign mentored = mentored | push: pub %}
        {% else %}
            {% assign others = others | push: pub %}
        {% endif %}
    {% endfor %}

    {% for publication in highlighted %}
        {% include publication.html %}
    {% endfor %}

    {% for publication in equal_contrib %}
        {% include publication.html %}
    {% endfor %}

    {% for publication in mentored %}
        {% include publication.html %}
    {% endfor %}

    {% for publication in others %}
        {% include publication.html %}
    {% endfor %}
{% endfor %}

</table>
