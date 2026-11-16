---
layout: default
title: Расписание
---

{% assign upcoming_events = site.posts
                          | where_exp: "event", "event.date >= site.time"
                          | sort: "date" %}

# Расписание

{% if upcoming_events.size == 0 %}
  <p>В ближайшее время мероприятий не будет.</p>
  <p>Не переживайте, следите за нашим расписанием в нашем <a href="tg://resolve?domain=devpraktika_channel">Telegram-канале</a> или на <a href="https://networkly.app/community/devpraktika">networkly</a>.</p>
{% else %}
  {% include events.html events=upcoming_events %}
{% endif %}
