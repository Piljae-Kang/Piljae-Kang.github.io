---
layout: archive
title: "Repositories"
permalink: /repositories/
author_profile: true
---

{{ site.data.repositories.description }}

<style>
.repo-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 1rem;
  margin-bottom: 1.25rem;
}

.repo-card {
  border: 1px solid #d0d7de;
  border-radius: 6px;
  padding: 1rem;
  background: #ffffff;
}

.repo-card-title {
  margin: 0 0 0.4rem 0;
  font-size: 1rem;
  font-weight: 600;
}

.repo-card-desc {
  margin: 0 0 0.8rem 0;
  min-height: 2.5rem;
  color: #57606a;
  font-size: 0.9rem;
}

.repo-meta {
  display: flex;
  gap: 0.75rem;
  color: #57606a;
  font-size: 0.85rem;
}
</style>

GitHub users
======
{% for user in site.data.repositories.users %}
### {{ user.username }}

{{ user.title }}
<div class="repo-grid">
  {% for repo in user.repositories %}
    <div class="repo-card">
      <h3 class="repo-card-title">
        <a href="https://github.com/{{ repo.owner }}/{{ repo.name }}" target="_blank" rel="noopener noreferrer">
          {{ repo.owner }}/{{ repo.name }}
        </a>
      </h3>
      <p class="repo-card-desc">{{ repo.description }}</p>
      <div class="repo-meta">
        {% if repo.language %}<span>{{ repo.language }}</span>{% endif %}
        <span>★ {{ repo.stars | default: 0 }}</span>
        <span>⑂ {{ repo.forks | default: 0 }}</span>
      </div>
    </div>
  {% endfor %}
</div>
{% endfor %}
