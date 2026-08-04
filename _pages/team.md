---
title: "Team"
layout: gridlay
sitemap: false
permalink: /team/
---

# Team

<p class="page-lead">Researchers connecting computational systems, data infrastructure, and accountable AI.</p>

{% if site.data.team_members.size > 0 %}
<div class="team-grid" markdown="0">
{% for member in site.data.team_members %}
<div class="team-card">
<div class="team-photo-frame">
<img src="{{ '/images/' | append: member.photo | relative_url }}" class="team-photo" alt="{{ member.name | escape }}" loading="lazy" width="320" height="320"{% if member.photo_position or member.photo_scale or member.photo_origin %} style="{% if member.photo_position %}object-position: {{ member.photo_position }};{% endif %}{% if member.photo_scale %} --photo-scale: {{ member.photo_scale }};{% endif %}{% if member.photo_origin %} --photo-origin: {{ member.photo_origin }};{% endif %}"{% endif %}>
</div>
<h2 class="team-name">{{ member.name | escape }}</h2>
{% if member.info %}<p class="team-info">{{ member.info }}</p>{% endif %}
{% if member.email or member.website or member.scholar or member.linkedin or member.github or member.orcid %}
<nav class="team-links" aria-label="{{ member.name | escape }} profiles">
{% if member.email %}<a href="mailto:{{ member.email }}" class="icon-link" aria-label="Email {{ member.name | escape }}" title="Email"><i class="fa-solid fa-envelope" aria-hidden="true"></i></a>{% endif %}
{% if member.website %}<a href="{{ member.website }}" class="icon-link" aria-label="{{ member.name | escape }} website" title="Website"><i class="fa-solid fa-house" aria-hidden="true"></i></a>{% endif %}
{% if member.scholar %}<a href="{{ member.scholar }}" class="icon-link" aria-label="{{ member.name | escape }} on Google Scholar" title="Google Scholar"><i class="ai ai-google-scholar" aria-hidden="true"></i></a>{% endif %}
{% if member.linkedin %}<a href="{{ member.linkedin }}" class="icon-link" aria-label="{{ member.name | escape }} on LinkedIn" title="LinkedIn"><i class="fa-brands fa-linkedin-in" aria-hidden="true"></i></a>{% endif %}
{% if member.github %}<a href="{{ member.github }}" class="icon-link" aria-label="{{ member.name | escape }} on GitHub" title="GitHub"><i class="fa-brands fa-github" aria-hidden="true"></i></a>{% endif %}
{% if member.orcid %}<a href="{{ member.orcid }}" class="icon-link" aria-label="{{ member.name | escape }} ORCID" title="ORCID"><i class="ai ai-orcid" aria-hidden="true"></i></a>{% endif %}
</nav>
{% endif %}
{% if member.bio %}
<details class="team-bio">
<summary>Biography</summary>
<p>{{ member.bio }}</p>
</details>
{% endif %}
</div>
{% endfor %}
</div>
{% endif %}

{% if site.data.prior_affiliates.size > 0 %}
<section class="prior-affiliates" aria-labelledby="prior-affiliates-title" markdown="0">
<div class="section-heading section-heading--compact">
<div>
<p class="eyebrow">Extended community</p>
<h2 id="prior-affiliates-title">Prior affiliates</h2>
</div>
<p>Researchers and collaborators previously affiliated with the Plale Lab.</p>
</div>
<ul class="affiliate-list">
{% for member in site.data.prior_affiliates %}
<li>
<span>{{ member.name }}</span>
{% if member.linkedin %}<a href="{{ member.linkedin }}" class="icon-link" aria-label="{{ member.name }} on LinkedIn" title="LinkedIn"><i class="fa-brands fa-linkedin-in" aria-hidden="true"></i></a>{% endif %}
</li>
{% endfor %}
</ul>
</section>
{% endif %}

{% if site.data.alumni.size > 0 %}
## Alumni

<div class="section-card">
<table class="alumni-table">
<thead>
<tr><th>Name</th><th>Duration</th><th>Current Position</th></tr>
</thead>
<tbody>
{% for member in site.data.alumni %}
<tr>
<td>{{ member.name }}</td>
<td>{{ member.duration }}</td>
<td>{{ member.info }}</td>
</tr>
{% endfor %}
</tbody>
</table>
</div>
{% endif %}
