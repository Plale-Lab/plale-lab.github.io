---
title: "News"
layout: gridlay
sitemap: false
permalink: /news/
---

## News

<div class="section-card" markdown="0">
<div class="news-timeline">
{% for article in site.data.news %}
<div class="news-item">
<span class="news-date">{{ article.date }}</span>
{% if article.category %}<span class="news-category">{{ article.category }}</span>{% endif %}
<span class="news-headline">{{ article.headline }}</span>
{% if article.body %}<p class="news-body">{{ article.body }}</p>{% endif %}
</div>
{% endfor %}
</div>
</div>
