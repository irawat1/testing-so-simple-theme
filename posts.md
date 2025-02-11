---
title: Posts
layout: posts
permalink: /posts/
show_excerpts: true
entries_layout: list
---

{% assign postsByYear = site.posts | group_by_exp:"post", "post.date | date: '%Y'" %}
{% assign years_count = postsByYear | size %}

{% if years_count > 2 %}
  <!-- Year-wise display for more than 2 years of posts -->
  {% for year in postsByYear %}
    <h2 id="{{ year.name }}" class="archive__subtitle">{{ year.name }}</h2>
    <div class="entries-{{ page.entries_layout | default: 'list' }}">
      {% for post in year.items %}
        {% include entry.html %}
      {% endfor %}
    </div>
  {% endfor %}
{% else %}
  <!-- Simple list for 2 years or fewer -->
  <div class="entries-{{ page.entries_layout | default: 'list' }}">
    {% assign sorted_posts = site.posts | sort: 'date' | reverse %}
    {% for post in sorted_posts %}
      {% include entry.html %}
    {% endfor %}
  </div>
{% endif %}
