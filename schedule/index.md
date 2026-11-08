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
  {% include events.html events=upcoming_events %}
{% endif %}
