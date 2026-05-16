---
layout: default
title: "Архив"
---

{% assign outgoing_events = site.events | where_exp: "event", "event.past == true" | sort: "date" %}

{% if outgoing_events.size == 0 %}
  <p class="text-muted">Нет прошедших событий.</p>
{% else %}
  <ul class="list-unstyled">
    {% for event in outgoing_events %}
      {% assign course = site.courses | where: "slug", event.course | first %}
      <li class="mb-3 border-bottom pb-3">
        <p class="mb-1">
          <a href="{{ event.url | relative_url }}">{{ course.title | default: event.course }}</a>
        </p>
        <p class="mb-1 text-muted small">
          {{ event.date | date: "%d.%m.%Y %H:%M" }}
        </p>
        <p class="mb-0">
          {% if event.educators %}
            {% for educator_slug in event.educators %}
              {% assign educator = site.educators | where: "slug", educator_slug | first %}
              {% if educator %}
                <img src="{{ educator.thumbnail }}" alt="{{ educator.givenName }} {{ educator.familyName }}" />
                <span>{{ educator.givenName }} {{ educator.familyName }}</span>{% unless forloop.last %}, {% endunless %}
              {% endif %}
            {% endfor %}
          {% endif %}
        </p>
      </li>
    {% endfor %}
  </ul>
{% endif %}
