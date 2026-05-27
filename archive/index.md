---
layout: default
title: "Архив"
---

{% assign outgoing_events = site.events | where_exp: "event", "event.past == true" | sort: "date" %}

{% if outgoing_events.size == 0 %}
  <p class="text-muted">Мы пока ничего не проводили.</p>
{% else %}
  <div class="row">
  {% for event in outgoing_events %}
    {% assign workshop = site.workshops | where: "slug", event.workshop | first %}
    <div class="col-sm-6 col-md-4">
      <div class="rounded-block mb-3">
        <p class="small">{{ event.date | date: "%d.%m.%Y" }} {{ event.date | date: "%H:%M" }}</p>
        <p class="fw-bold fs-5 mb-1"><a class="text-black" href="{{ event.url | relative_url }}">{{ workshop.title | default: event.workshop }}</a></p>
        <p class="mb-1">{{ workshop.description }}</p>
      </div>
      <div class="rounded-block">
        <div class="row">
        {% if event.educators %}
          {% for educator_slug in event.educators %}
            {% assign educator = site.educators | where: "slug", educator_slug | first %}
            {% if educator %}
              <div class="col-6 text-center">
                <img class="educator" src="{{ educator.thumbnail }}" alt="{{ educator.givenName }} {{ educator.familyName }}" ><br />
                <strong>{{ educator.givenName }} {{ educator.familyName }}</strong>
              </div>
            {% endif %}
          {% endfor %}
        {% endif %}
        </div>
      </div>
    </div>
  {% endfor %}
  </div>
{% endif %}
