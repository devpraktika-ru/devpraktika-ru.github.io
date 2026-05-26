---
layout: default
title: "Практикумы"
---

<ul>
  {% for workshop in site.workshops %}
    <li>
      <a href="{{ workshop.url | relative_url }}">
        {{ workshop.title }}
      </a>
      <p><em>{{ workshop.description }}</em></p>
    </li>
  {% endfor %}
</ul>