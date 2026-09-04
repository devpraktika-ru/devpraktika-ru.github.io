---
layout: default
title: "Ведущие"
---

{% assign sorted_educators = site.educators | sort: "givenName" | sort: "familyName" %}

# Ведущие

Мы познакомились в <a href="https://prog.msk.ru">Московском клубе программистов</a>.

Каждый ведущий так или иначе участвовал в деятельности клуба: делал доклады, записывал видеоуроки, проводил воркшопы, организовывал ретриты.

Хотите понять, подходит ли вам ведущий?
Посмотрите пару его видео.
Посмотрите видео разных ведущих, чтобы выбрать того, кто больше вам импонирует.

<div class="row w-100">
  {% for educator in sorted_educators %}
    <div class="col-6 bg-white mb-1 text-center">
      <p class="fw-bold fs-5 mb-1"><a class="text-black" href="{{ educator.url | relative_url }}">{{ educator.givenName }} {{ educator.familyName }}</a></p>
      <img class="educator" src="{{ educator.thumbnail }}" alt="{{ educator.givenName }} {{ educator.familyName }}" />
      <p><em>{{ educator.description }}</em></p>
    </div>
  {% endfor %}
</div>
