---
title: "Contact"
layout: gridlay
sitemap: false
permalink: /contact/
---

## Contact

<div class="section-card" markdown="0">

<h4>Email</h4>
<p><a href="mailto:{{ site.email | escape }}"><i class="fa-solid fa-envelope"></i> {{ site.email | escape }}</a></p>

<h4>Institution</h4>
<p>{{ site.name | escape }}, {{ site.title | escape }}<br>{{ site.institution | escape }}</p>

{% if site.links.google_scholar and site.links.google_scholar != "" or site.links.github and site.links.github != "" or site.links.researchgate and site.links.researchgate != "" or site.links.orcid and site.links.orcid != "" or site.links.twitter and site.links.twitter != "" or site.links.linkedin and site.links.linkedin != "" %}
<h4>Social</h4>
<div style="display: flex; gap: var(--space-2); flex-wrap: wrap;">
{% if site.links.google_scholar and site.links.google_scholar != "" %}<a href="{{ site.links.google_scholar }}" class="icon-link" title="Google Scholar"><i class="ai ai-google-scholar"></i></a>{% endif %}
{% if site.links.github and site.links.github != "" %}<a href="{{ site.links.github }}" class="icon-link" title="GitHub"><i class="fa-brands fa-github"></i></a>{% endif %}
{% if site.links.researchgate and site.links.researchgate != "" %}<a href="{{ site.links.researchgate }}" class="icon-link" title="ResearchGate"><i class="ai ai-researchgate"></i></a>{% endif %}
{% if site.links.orcid and site.links.orcid != "" %}<a href="{{ site.links.orcid }}" class="icon-link" title="ORCID"><i class="ai ai-orcid"></i></a>{% endif %}
{% if site.links.twitter and site.links.twitter != "" %}<a href="{{ site.links.twitter }}" class="icon-link" title="Twitter"><i class="fa-brands fa-twitter"></i></a>{% endif %}
{% if site.links.linkedin and site.links.linkedin != "" %}<a href="{{ site.links.linkedin }}" class="icon-link" title="LinkedIn"><i class="fa-brands fa-linkedin"></i></a>{% endif %}
</div>
{% endif %}

</div>
