---
layout: default
title: "Практикумы"
---

<div class="row">
  <div class="bg-white col-12 mb-3">
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

<div class="row bg-white">
  {% for workshop in site.workshops %}
    <div class="col-4 mb-1 text-center">
      <p class="fw-bold fs-5 mb-1"><a class="text-black" href="{{ workshop.url | relative_url }}">{{ workshop.title }}</a></p>
      <p><em>{{ workshop.description }}</em></p>
    </div>
  {% endfor %}
</div>
