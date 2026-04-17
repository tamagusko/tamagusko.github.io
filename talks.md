---
layout: page
title: Talks
permalink: /talks.html
published: false   # flip to true (and re-enable nav link in _includes/header.html) when content is ready
---

{% assign talks = site.data.talks | where_exp: "t", "t.title" %}

{% if talks.size == 0 %}

No public talks listed yet. For invited-talk requests, see the [contact options](/) on the home page.

{% else %}

<ul class="talks">
{% for t in talks %}
  <li>
    <span class="talk-date">{{ t.date | date: "%Y-%m-%d" }}</span>
    <span class="talk-title">{{ t.title }}</span>
    <span class="talk-meta">
      {% if t.type %}<span class="talk-type">{{ t.type }}</span>{% endif %}
      <span class="talk-venue">{{ t.venue }}{% if t.location %} · {{ t.location }}{% endif %}</span>
    </span>
    {% if t.slides_url or t.video_url or t.event_url %}
    <span class="talk-links">
      {% if t.slides_url %}<a href="{{ t.slides_url }}" rel="noopener external">slides</a>{% endif %}
      {% if t.video_url %}<a href="{{ t.video_url }}" rel="noopener external">video</a>{% endif %}
      {% if t.event_url %}<a href="{{ t.event_url }}" rel="noopener external">event</a>{% endif %}
    </span>
    {% endif %}
  </li>
{% endfor %}
</ul>

{% endif %}
