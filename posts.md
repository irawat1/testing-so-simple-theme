---
title: Posts
layout: posts
permalink: /posts/
show_excerpts: true
entries_layout: list
---

{% assign postsByYear = site.posts | group_by_exp:"post", "post.date | date: '%Y'" %}

{% if postsByYear.size > 2 %}
  <!-- Year-wise display for more than 2 years of posts -->
  {% for year in postsByYear %}
  <h2 id="{{ year.name }}" class="archive__subtitle">{{ year.name }}</h2>
  {% for post in year.items %}
    {% include post-list.html %}
  {% endfor %}
  {% endfor %}
{% else %}
  <!-- Simple list for 2 years or fewer -->
  {% for post in site.posts %}
    {% include post-list.html %}
  {% endfor %}
{% endif %}
