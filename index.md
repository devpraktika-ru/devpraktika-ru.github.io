---
layout: default
---

{% assign upcoming_events = site.posts | where_exp: "event", "event.date >= site.time" | sort: "date" %}

# Практикумы для программистов

<div class="home-intro" markdown="1">

![Практикумы для программистов](https://github.com/user-attachments/assets/dbd410bd-6927-463b-ad68-f70a17a9425b){: .home-illustration  width="1200" height="900"}

Архитектурные воркшопы, лайв-кодинг, быстрое введение в языки программирования — по вечерам и в выходные.

Пишем небольшие проекты промышленного уровня.
Прорабатываем архитектуру веб-приложений.
Решаем задачи, практикуя подход «сначала тесты».

У наших ведущих большой практический опыт и — кроме того — статьи на Хабре, видеоуроки в YouTube, ответы на Stack Overflow и бесчисленные воркшопы.
</div>

{% if upcoming_events.size == 0 %}
  <p class="border border-secondary border-dashed p-3">
    В ближайшее время мероприятий не будет.
    Не переживайте, следите за нашим расписанием на <a href="https://networkly.app/community/devpraktika">networkly</a>.
  </p>
{% else %}
  <h2>Ближайшие встречи</h2>
  <div class="card-list">
  {% for event in upcoming_events limit: 3 %}
    {% assign workshop = site.workshops | where: "slug", event.slug | first %}
    <article>
      <p class="fs-5"><a class="text-black" href="{{ event.url |   relative_url }}">{{ workshop.title }}</a></p>
      <p class="small">📅 {{ event.date | date: "%d.%m.%Y" }} ⏰ {{ event.date | date: "%H:%M" }}</p>
      <p><em>{{ event.description }}</em></p>
      {% if event.price > 0 %}
        <p class="fs-4 text-end price">{{ event.price }}₽</p>
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
