---
title: "Publications"
layout: gridlay
sitemap: false
permalink: /publications/
---

## Publications

<div markdown="0"><input type="text" class="pub-search" id="pubSearch" placeholder="Filter by title, author, or year..."></div>

{% assign has_media = site.data.media.size | default: 0 %}
<div class="{% if has_media > 0 %}home-grid{% endif %}">
<div class="{% if has_media > 0 %}home-content{% endif %}">

<div class="section-card" id="pubList">
<h3>Preprints</h3>

{% bibliography --query @unpublished %}

<h3>Publications</h3>

{% bibliography --query !@unpublished %}

</div>
</div>

{% if has_media > 0 %}
<div>
<h3>In the media</h3>
<div class="section-card">
<div class="news-timeline">
{% for mention in site.data.media %}
<div class="news-item">
<span class="news-date">{{ mention.date }}</span>
<a class="news-headline" href="{{ mention.url }}" target="_blank" rel="noopener">{{ mention.title }}</a>
{% if mention.outlet %}<p class="news-body">{{ mention.outlet }}</p>{% endif %}
</div>
{% endfor %}
</div>
</div>
</div>
{% endif %}

</div>
