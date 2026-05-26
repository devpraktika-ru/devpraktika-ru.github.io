---
layout: default
title: dev praktika
---

{% assign upcoming_events = site.events | where_exp: "event", "event.past == false" | sort: "date" %}

<div class="main-intro">
  <h1>Практикум для <br />
  мидлов и сеньоров</h1>

  <p>Архитектурные воркшопы, код-ретриты, быстрое введение в языки программирования — по вечерам и в выходные.</p>

  <p>Учим, делая в командах небольшие проекты промышленного уровня.
  У наших ведущих — большой практический опыт и желание им делится.</p>
</div>

{% if upcoming_events.size == 0 %}
  <p class="text-muted mb-0">В ближайшее время ничего не будет.</p>
{% else %}
  <h2>Ближайшие курсы и воркшопы</h2>
  <ul class="list-unstyled mb-0">
    {% for event in upcoming_events limit:3 %}
      {% assign workshop = site.workshops | where: "slug", event.workshop | first %}
      <li class="mb-3 border-bottom pb-3">
        <p class="mb-1">
          <a href="{{ event.url | relative_url }}">{{ workshop.title | default: event.workshop }}</a>
        </p>
        <p class="mb-1 text-muted small">
          {{ event.date | date: "%d.%m.%Y %H:%M" }}
          {% if event.price != nil %}· {{ event.price }}{% endif %}
        </p>
        <p class="mb-0 small">
          {% if event.educators %}
            {% for educator_slug in event.educators %}
              {% assign educator = site.educators | where: "slug", educator_slug | first %}
              {% if educator %}
                <span>{{ educator.givenName }} {{ educator.familyName }}</span>{% unless forloop.last %}, {% endunless %}
              {% endif %}
            {% endfor %}
          {% endif %}
        </p>
      </li>
    {% endfor %}
  </ul>
{% endif %}
