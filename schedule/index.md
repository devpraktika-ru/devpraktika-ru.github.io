---
layout: default
title: "Расписание"
---

{% assign upcoming_events = site.posts | where_exp: "event", "event.past == false" | sort: "date" %}

# Расписание

{% if upcoming_events.size == 0 %}
  <p>
    В ближайшее время мероприятий не будет.
    Не переживайте, следите за нашим расписанием на networkly.
  </p>
{% else %}
  {% for event in upcoming_events %}
    {% assign workshop = site.workshops | where: "slug", event.  workshop | first %}
    <article class="mb-4">
      <h3><a class="text-black" href="{{ event.url |   relative_url }}">{{ workshop.title }}</a></h3>
      <p class="small">📅 {{ event.date | date: "%d.%m.%Y" }} ⏰ {{ event.date | date: "%H:%M" }}</p>
      <p>{{ workshop.description }}</p>
      <p class="fs-3 text-end price">
        {% if event.price == 0 %}
          бесплатно
        {% else %}
          {{ event.price }}₽
        {% endif %}
      </p>
      <div class="row">
        {% for educator_slug in event.educators %}
          {% assign educator = site.educators | where: "slug",   educator_slug | first %}
          <div class="col text-center">
            <img class="img-thumbnail" src="{{ educator.  thumbnail }}" alt="{{ educator.givenName }} {{   educator.familyName }}" width="80" height="80">
            <p>{{ educator.givenName }} {{ educator.familyName }}  </p>
          </div>
        {% endfor %}
      </div>
    </article>
  {% endfor %}
{% endif %}
