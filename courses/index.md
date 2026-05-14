---
layout: default
title: "Курсы"
---

<ul>
  {% for course in site.courses %}
    <li>
      <a href="{{ course.url | relative_url }}">
        {{ educator.title }}
      </a>
    </li>
  {% endfor %}
</ul>