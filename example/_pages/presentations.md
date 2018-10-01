---
title: "Presentations"
layout: archive
permalink: /presentations/
author_profile: true
classes: wide
---
{% assign docs = site.documents | where:"research","true" %}
{% for post in docs %}
  <article class="archive__item" itemscope itemtype="http://schema.org/CreativeWork">
  <h2 class="archive__item-title" itemprop="headline">
  <a href="{{ post.url | relative_url }}" rel="permalink">{{ post.title }}</a>
  </h2>
    <h4>{{ post.author }}</h4>
    <p>{{ post.abstract | truncatewords: 75 }}</p>
  </article>
{% endfor %}
