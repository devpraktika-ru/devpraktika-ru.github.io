---
layout: default
title: dev praktika
---

{% assign upcoming_events = site.events | where_exp: "event", "event.past == false" | sort: "date" %}

<div class="row main-intro">
  <div class="col-8">
    <h1>Практикум для <br />
    мидлов и сеньоров</h1>

    <p>Архитектурные воркшопы, код-ретриты, быстрое введение в языки программирования — по вечерам и в выходные.</p>

    <p>Пишем небольшие проекты промышленного уровня.
    Проектируем архитектуру веб-приложений.
    Решаем задачи, практикуя подход «сначала тесты».</p>

    <p>У наших ведущих большой практический опыт, а также статьи на Хабре, видеоуроки в YouTube и ответы на Stack Overflow.</p>
  </div>
</div>

{% if upcoming_events.size == 0 %}
  <p class="text-muted mb-0">В ближайшее время ничего не будет.</p>
{% else %}
  <h2>Ближайшие практикумы</h2>
  <div class="row">
  {% for event in upcoming_events limit:3 %}
    {% assign workshop = site.workshops | where: "slug", event.workshop | first %}
    <div class="col-sm-6 col-md-4">
      <div class="card mb-3">
        <p class="small">{{ event.date | date: "%d.%m.%Y" }} {{ event.date | date: "%H:%M" }}</p>
        <p class="fw-bold fs-5 mb-1"><a class="text-black" href="{{ event.url | relative_url }}">{{ workshop.title | default: event.workshop }}</a></p>
        <p class="mb-1">{{ workshop.description }}</p>
        <p class="fs-3 text-end">{{ event.price }}₽</p>
      </div>
      <div class="card">
        {% if event.educators %}
          {% for educator_slug in event.educators %}
            {% assign educator = site.educators | where: "slug", educator_slug | first %}
            {% if educator %}
              <div class="col-6 text-center">
                <img src="{{ educator.thumbnail }}" alt="{{ educator.givenName }} {{ educator.familyName }}" ><br />
                <strong>{{ educator.givenName }} {{ educator.familyName }}</strong>
              </div>
            {% endif %}
          {% endfor %}
        {% endif %}
      </div>
    </div>
  {% endfor %}
  </div>
{% endif %}
