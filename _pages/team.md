---
title: "Team"
layout: gridlay
sitemap: false
permalink: /team/
---

# Team

<p class="page-lead">Researchers connecting computational systems, data infrastructure, and accountable AI.</p>

{% if site.data.team_members.size > 0 %}
<div class="team-grid">
{% for member in site.data.team_members %}
<div class="team-card">
<img src="{{ '/images/' | append: member.photo | relative_url }}" class="team-photo" alt="{{ member.name }}" loading="lazy">
<h2 class="team-name">{{ member.name }}</h2>
{% if member.info %}<p class="team-info">{{ member.info }}</p>{% endif %}
{% if member.email or member.website or member.scholar or member.github or member.orcid %}
<nav class="team-links" aria-label="{{ member.name }} profiles">
{% if member.email %}<a href="mailto:{{ member.email }}" class="icon-link" aria-label="Email {{ member.name }}" title="Email"><i class="fa-solid fa-envelope" aria-hidden="true"></i></a>{% endif %}
{% if member.website %}<a href="{{ member.website }}" class="icon-link" aria-label="{{ member.name }} website" title="Website"><i class="fa-solid fa-house" aria-hidden="true"></i></a>{% endif %}
{% if member.scholar %}<a href="{{ member.scholar }}" class="icon-link" aria-label="{{ member.name }} on Google Scholar" title="Google Scholar"><i class="ai ai-google-scholar" aria-hidden="true"></i></a>{% endif %}
{% if member.github %}<a href="{{ member.github }}" class="icon-link" aria-label="{{ member.name }} on GitHub" title="GitHub"><i class="fa-brands fa-github" aria-hidden="true"></i></a>{% endif %}
{% if member.orcid %}<a href="{{ member.orcid }}" class="icon-link" aria-label="{{ member.name }} ORCID" title="ORCID"><i class="ai ai-orcid" aria-hidden="true"></i></a>{% endif %}
</nav>
{% endif %}
</div>
{% endfor %}
</div>
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
