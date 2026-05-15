---
layout: main
---

{% assign upcoming_events = site.events | where_exp: "event", "event.past == false" | sort: "date" %}

<div class="row g-4">
  <div class="col-12 col-lg-8">
    <h1 class="h2 mb-3">dev•praktika</h1>
    <p>
      Практические занятия и воркшопы по разработке, архитектуре и командной работе.
      Выберите ближайшее событие в расписании справа или перейдите в разделы с курсами и ведущими.
    </p>
  </div>
  <div class="col-12 col-lg-4">
    <h2 class="h5 mb-3">Ближайшие события</h2>

    {% if upcoming_events.size == 0 %}
      <p class="text-muted mb-0">Нет предстоящих событий.</p>
    {% else %}
      <ul class="list-unstyled mb-0">
        {% for event in upcoming_events limit:3 %}
          {% assign course = site.courses | where: "slug", event.course | first %}
          <li class="mb-3 border-bottom pb-3">
            <p class="mb-1">
              <a href="{{ event.url | relative_url }}">{{ course.title | default: event.course }}</a>
            </p>
            <p class="mb-1 text-muted small">
              {{ event.date | date: "%d.%m.%Y %H:%M" }}
              {% if event.price != nil %}· {{ event.price }}{% endif %}
            </p>
            <p class="mb-0 small">
              {% if event.educators %}
                {% for educator_slug in event.educators %}
                  {% assign educator = site.educators | where: "slug", educator_slug | first %}
                  {% if educator %}
                    <span>{{ educator.givenName }} {{ educator.familyName }}</span>{% unless forloop.last %}, {% endunless %}
                  {% endif %}
                {% endfor %}
              {% endif %}
            </p>
          </li>
        {% endfor %}
      </ul>
    {% endif %}
  </div>
</div>
