---
layout: default
---

{% assign upcoming_events = site.posts
                          | where_exp: "event", "event.date >= site.time"
                          | sort: "date"
                          | slice: 0, 3 %}

# Практикумы для программистов

<div class="home-intro" markdown="1">
![Практикумы для программистов](https://github.com/user-attachments/assets/dbd410bd-6927-463b-ad68-f70a17a9425b){: .align-top-with-text width="1200" height="900"}

Архитектурные воркшопы, лайв-кодинг, быстрое введение в языки программирования — по вечерам и в выходные.

Пишем небольшие проекты промышленного уровня, прорабатываем архитектуру, решаем задачи.

Работаем в малых группах, разбираем задачи и решения участников, отвечаем на вопросы.

У наших ведущих большой практический опыт и — кроме того — статьи на Хабре, видеоуроки в YouTube и десятки проведённых воркшопов.

Чтобы познакомиться с нашими форматами, смотрите записи наших встреч в <a href="https://youtube.com/@devpraktika">YouTube</a> и в <a href="https://vkvideo.ru/@devpraktika">VK Видео</a>.
</div>

{% include subscribe.html %}

{% if upcoming_events.size == 0 %}
  <p>В ближайшее время мероприятий не будет.</p>
  <p>Не переживайте, следите за нашим расписанием в нашем <a href="tg://resolve?domain=devpraktika_channel">Telegram-канале</a> или на <a href="https://networkly.app/community/devpraktika">networkly</a>.</p>
{% else %}
  <h2>Ближайшие встречи</h2>
  {% include events.html events=upcoming_events %}
  <p>Следить за анонсами новых мероприятий можно в нашем <a href="tg://resolve?domain=devpraktika_channel">Telegram-канале</a> или на <a href="https://networkly.app/community/devpraktika">networkly</a>.</p>
{% endif %}
