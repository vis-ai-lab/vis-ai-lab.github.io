---
layout: default
title: VisAI Lab | Home
---

<div class="home-layout">
  <div class="home-main">
    <h1>HKUST Visualization and Artificial Intelligence Lab</h1>
    <span>The VisAI Lab studies at the intersection of visualization and artificial intelligence, with special emphasis on biomedical applications.</span>
    <div class="home-section">
      <h2 id="research-themes" data-copy-section><span class="section-name">Research Themes</span></h2>
      <div class="areas">
          {% assign areas = site.areas | sort: 'order' %}
          {% for area in areas %}
          {% include area.html %}
          {% endfor %}
      </div>
    </div>

    <div class="home-section">
      <h2 id="featured-papers" data-copy-section><span class="section-name">Featured Papers</span> <small><a href="/papers">[see more]</a></small></h2>

      <table class="publications">
          {% assign featured_publications = site.publications | where: 'featured', true | sort: 'year' | reverse | slice: 0,10 %}
          {% for publication in featured_publications %}
          {% include publication.html %}
          {% endfor %}
      </table>
    </div>

  </div>

  <aside class="home-sidebar">
    <section class="sidebar-section members-section">
      <h2 id="members" data-copy-section><span class="section-name">Members</span></h2>
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
        <h2 id="news" data-copy-section><span class="section-name">News</span> <small><a href="{{ '/news' | relative_url }}">[see more]</a></small></h2>
      </div>
      <div class="news-cards">
        {% assign latest_news = site.news | where_exp: "item", "item.type != 'SERVICE'" | sort: 'date' | reverse | slice: 0,7 %}
        {% for news in latest_news %}
        {% include news-card.html %}
        {% endfor %}
      </div>
    </section>
  </aside>
</div>

<script>
  var siteHeader = document.querySelector('header');

  function updateHeaderHeight() {
    if (!siteHeader) return;
    document.documentElement.style.setProperty('--header-height', siteHeader.offsetHeight + 'px');
  }

  updateHeaderHeight();

  if (siteHeader && 'ResizeObserver' in window) {
    new ResizeObserver(updateHeaderHeight).observe(siteHeader);
  } else {
    window.addEventListener('resize', updateHeaderHeight);
  }

  document.querySelectorAll('[data-copy-section]').forEach(function(heading) {
    heading.addEventListener('click', function(event) {
      if (event.target.closest('a')) return;

      updateHeaderHeight();
      window.location.hash = heading.id;
      navigator.clipboard.writeText(window.location.href);
    });
  });

  if (window.location.hash) {
    requestAnimationFrame(function() {
      var target = document.querySelector(window.location.hash);
      if (target) target.scrollIntoView();
    });
  }
</script>
