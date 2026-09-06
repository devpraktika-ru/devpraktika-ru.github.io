---
layout: default
title: dev praktika
---

{% assign upcoming_events = site.posts | where_exp: "event", "event.date >= site.time" | sort: "date" %}

# Практикум для мидлов и сеньоров

Архитектурные воркшопы, код-ретриты, быстрое введение в языки программирования — по вечерам и в выходные.

Пишем небольшие проекты промышленного уровня. Проектируем архитектуру веб-приложений. Решаем задачи, практикуя подход «сначала тесты».

У наших ведущих большой практический опыт и — кроме того — статьи на Хабре, видеоуроки в YouTube и ответы на Stack Overflow.

{% if upcoming_events.size == 0 %}
  <p class="border border-secondary border-dashed p-3">
    В ближайшее время мероприятий не будет.
    Не переживайте, следите за нашим расписанием на networkly.
  </p>
{% else %}
  <h2>Ближайшие встречи</h2>
  {% for event in upcoming_events limit: 3 %}
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