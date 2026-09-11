---
layout: default
title: Расписание
---

{% assign upcoming_events = site.posts | where_exp: "event", "event.date >= site.time" | sort: "date" %}


# Расписание

{% if upcoming_events.size == 0 %}
  <p class="border border-secondary border-dashed p-3">
    В ближайшее время мероприятий не будет.
    Не переживайте, следите за нашим расписанием на <a href="https://networkly.app/community/devpraktika">networkly</a>.
  </p>
{% else %}
  <div class="card-list">
  {% for event in upcoming_events %}
    {% assign workshop = site.workshops | where: "slug", event.  workshop | first %}
    <article>
      <p class="fs-5"><a class="text-black" href="{{ event.url |   relative_url }}">{{ workshop.title }}</a></p>
      <p class="small">📅 {{ event.date | date: "%d.%m.%Y" }} ⏰ {{ event.date | date: "%H:%M" }}</p>
      <p><em>{{ workshop.description }}</em></p>
      {% if event.price == 0 %}
        <p class="price">Мероприятие бесплатное.</p>
      {% else %}
        <p>Стоимость: <span class="price">{{ event.price }}₽</span>.</p>
      {% endif %}
      <div class="row">
        {% for educator_slug in event.educators %}
          {% assign educator = site.educators | where: "slug",   educator_slug | first %}
          <div class="col text-center">
            <img src="{{ educator.thumbnail }}" alt="{{ educator.title }}" width="90" height="120">
            <p>{{ educator.title }}</p>
          </div>
        {% endfor %}
      </div>
    </article>
  {% endfor %}
  </div>
{% endif %}
