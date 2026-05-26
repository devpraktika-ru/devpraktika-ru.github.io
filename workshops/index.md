---
layout: default
title: "Воркшопы"
---

<ul>
  {% for workshop in site.workshop %}
    <li>
      <a href="{{ workshop.url | relative_url }}">
        {{ workshop.title }}
      </a>
      <p><em>{{ workshop.description }}</em></p>
    </li>
  {% endfor %}
</ul>