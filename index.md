---
layout: default
title: VisAI Lab | Home
---

<div class="home-layout">
  <div class="home-main">
    <h1>HKUST Visualization and Artificial Intelligence Lab</h1>
    <span>The VisAI Lab studies at the intersection of visualization and artificial intelligence, with special emphasis on biomedical applications.</span>
    <div class="home-section">
      <h2 id="research-themes" data-copy-section>Research Themes</h2>
      <div class="areas">
          {% assign areas = site.areas | sort: 'order' %}
          {% for area in areas %}
          {% include area.html %}
          {% endfor %}
      </div>
    </div>

    <div class="home-section">
      <h2 id="selected-papers" data-copy-section>Selected Papers <small><a href="/papers">[see more]</a></small></h2>

      <table class="publications">
          {% assign featured_publications = site.publications | where: 'featured', true | sort: 'year' | reverse | slice: 0,10 %}
          {% for publication in featured_publications %}
          {% include publication.html %}
          {% endfor %}
      </table>
    </div>

    <div class="home-section">
      <h2 id="media-coverage" data-copy-section>Media Coverage</h2>
      <table class='media'>
          <tr>
              <td>
                  <div class='media-source'>
                      <img class='media-nature-icon' src='assets/nature.png' alt=""/>
                      <strong>Nature</strong> (TECHNOLOGY FEATURE)
                  </div>
                  <div class='media-title'>
                      <a href="https://www.nature.com/articles/d41586-022-02191-z">
                          A graphics toolkit for visualizing genome data
                      </a>
                  </div>
                  <div class='media-subtitle'>
                      Powerful 'grammar' allows geneticists to display their data in interactive and scalable illustrations.
                  </div>
              </td>
          </tr>
      </table>
    </div>
  </div>

  <aside class="home-sidebar">
    <section class="sidebar-section members-section">
      <h2 id="members" data-copy-section>Members</h2>
      <div class="member-list">
        {% assign members = site.members | sort: 'order' %}
        {% for member in members %}
        <a class="member-card" href="{{ member.website | default: member.url }}">
          {% if member.image %}
          <img class="member-photo" src="{{ 'assets/' | append: member.image | relative_url }}" alt="{{ member.name }}">
          {% endif %}
          <div class="member-info">
            <div class="member-name">{{ member.name }}</div>
            <div class="member-role">{{ member.role }}</div>
          </div>
        </a>
        {% endfor %}
      </div>
    </section>

    <section class="sidebar-section news-section">
      <div class="news-section-header">
        <h2 id="news" data-copy-section>News <small><a href="{{ '/news' | relative_url }}">[see more]</a></small></h2>
      </div>
      <div class="news-cards">
        {% assign latest_news = site.news | where_exp: "item", "item.type != 'SERVICE'" | sort: 'date' | reverse | slice: 0,8 %}
        {% for news in latest_news %}
        {% include news-card.html %}
        {% endfor %}
      </div>
    </section>
  </aside>
</div>

<script>
  document.querySelectorAll('[data-copy-section]').forEach(function(heading) {
    heading.addEventListener('click', function(event) {
      if (event.target.closest('a')) return;

      var url = window.location.origin + window.location.pathname + '#' + heading.id;
      navigator.clipboard.writeText(url);
    });
  });
</script>
