---
layout: default
title: "Практикумы"
---

# Практикумы

Откуда берутся темы?
Из жизни.
Архитектурные воркшопы — основаны на реальных событиях.
За код-ретритами — живая боль освоения TDD.
Интернет-магазин?
Да, мы такой писали!

Кроме того, мы постоянно работаем над новыми темами.

<div class="card-list">
{% for workshop in site.workshops %}
  <article>
    <p class="fs-5"><a class="text-black" href="{{ workshop.url | relative_url }}">{{ workshop.title }}</a></p>
    <p><em>{{ workshop.description }}</em></p>
  </article>
{% endfor %}
</div>
