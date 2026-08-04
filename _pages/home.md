---
title: "Home"
layout: homelay
sitemap: false
permalink: /
---

<section class="home-hero-band" aria-labelledby="home-title" markdown="0">
  <div class="home-hero-inner">
    <div class="home-hero-brand">
      <img src="{{ '/images/brand/plalelab-logo-primary.svg' | relative_url }}" alt="PlaleLab — Traceable Intelligence" class="home-hero-logo home-hero-logo--light">
      <img src="{{ '/images/brand/plalelab-logo-reverse.svg' | relative_url }}" alt="PlaleLab — Traceable Intelligence" class="home-hero-logo home-hero-logo--dark">
    </div>

    <div class="home-hero-message">
      <p class="eyebrow">Research infrastructure for accountable AI</p>
      <h1 id="home-title">From systems <br>to evidence.</h1>
      <p class="home-hero-lead">We build the connective tissue between computation, data, metadata, and the evidence needed to make AI reproducible and accountable.</p>
      <div class="home-hero-actions">
        <a class="button button--primary" href="https://github.com/Plale-Lab"><i class="fa-brands fa-github" aria-hidden="true"></i> Explore GitHub</a>
        <a class="button button--secondary" href="#projects">View projects <i class="fa-solid fa-arrow-down" aria-hidden="true"></i></a>
      </div>
    </div>

    <div class="trace-panel" aria-label="Research path from infrastructure to accountability">
      <p class="trace-panel__label">Research path</p>
      <ol>
        <li><span>01</span><strong>Infrastructure</strong></li>
        <li><span>02</span><strong>Data</strong></li>
        <li><span>03</span><strong>Metadata</strong></li>
        <li><span>04</span><strong>Evidence</strong></li>
        <li class="is-evidence"><span>05</span><strong>Accountability</strong></li>
      </ol>
    </div>
  </div>
</section>

<section class="home-work" id="projects" aria-labelledby="projects-title" markdown="0">
  <header class="section-heading">
    <div>
      <p class="eyebrow">Selected systems &amp; research</p>
      <h2 id="projects-title">Work you can inspect.</h2>
    </div>
    <p>Code, documentation, datasets, and papers stay close to the claims they support.</p>
  </header>

  <div class="home-work-grid">
    <div class="project-ledger">
      {% assign featured_projects = site.data.projects | where: "featured", true | sort: "order" %}
      {% for project in featured_projects %}
        {% include project-entry.html project=project index=forloop.index %}
      {% endfor %}
    </div>

    <aside class="home-news" aria-labelledby="news-title">
      <div class="home-news__header">
        <div>
          <p class="eyebrow">Selected signals</p>
          <h2 id="news-title">News</h2>
        </div>
        <a href="{{ '/news/' | relative_url }}">All news <span aria-hidden="true">→</span></a>
      </div>
      {% include news-list.html limit=3 %}
    </aside>
  </div>
</section>
