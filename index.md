---
layout: default
---

{% assign upcoming_events = site.posts | where_exp: "event", "event.date >= site.time" | sort: "date" %}
{% assign upcoming_events = upcoming_events | slice: 0, 3 %}

# Практикумы для программистов

<div class="home-intro" markdown="1">

![Практикумы для программистов](https://github.com/user-attachments/assets/dbd410bd-6927-463b-ad68-f70a17a9425b){: .align-top-with-text width="1200" height="900"}

Архитектурные воркшопы, лайв-кодинг, быстрое введение в языки программирования — по вечерам и в выходные.

Пишем небольшие проекты промышленного уровня, прорабатываем архитектуру, решаем задачи, практикуя подход «сначала тесты».

У наших ведущих большой практический опыт и — кроме того — статьи на Хабре, видеоуроки в YouTube и десятки воркшопов.
</div>

{% if upcoming_events.size == 0 %}
  <p class="border border-secondary border-dashed p-3">
  В ближайшее время мероприятий не будет.
  Не переживайте, следите за нашим расписанием в нашем <a href="https://t.me/devpraktika_channel">Telegram-канале</a> или на <a href="https://networkly.app/community/devpraktika">networkly</a>.
  </p>
{% else %}
  <h2>Ближайшие встречи</h2>
  {% include events.html events=upcoming_events %}
  <p>
    Следить за анонсами новых мероприятий можно в нашем <a href="https://t.me/devpraktika_channel">Telegram-канале</a> или на <a href="https://networkly.app/community/devpraktika">networkly</a>.
  </p>
{% endif %}
