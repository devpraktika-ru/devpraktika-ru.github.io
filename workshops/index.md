---
layout: default
title: "Практикумы"
---

<div class="row">
  <div class="rounded-block col-12 mb-3 w-100">
    <h1>Практикумы</h1>

    <p>Откуда берутся темы?
    Из жизни.
    Архитектурные воркшопы — основаны на реальных событиях.
    За код-ретритами — живая боль освоения TDD.
    Интернет-магазин?
    Да, мы такой писали!</p>

    <p>Кроме того, мы постоянно работаем над новыми темами.</p>
  </div>
</div>

<div class="row rounded-block w-100">
  {% for workshop in site.workshops %}
    <div class="col-6 text-center mb-1">
      <p class="fw-bold fs-5 mb-1"><a class="text-black" href="{{ workshop.url | relative_url }}">{{ workshop.title }}</a></p>
      <p><em>{{ workshop.description }}</em></p>
    </div>
  {% endfor %}
</div>
