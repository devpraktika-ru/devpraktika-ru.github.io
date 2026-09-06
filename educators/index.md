---
layout: default
title: "Ведущие"
---

{% assign sorted_educators = site.educators | sort: "givenName" | sort: "familyName" %}

# Ведущие

Мы познакомились в <a href="https://prog.msk.ru">Московском клубе программистов</a>.

Каждый ведущий так или иначе участвовал в деятельности клуба: делал доклады, записывал видеоуроки, проводил воркшопы.

Хотите понять, подходит ли вам ведущий?
Посмотрите его видео.
Посмотрите видео разных ведущих, чтобы выбрать того, кто больше вам импонирует.

<div class="card-list">
{% for educator in sorted_educators %}
  <article>
    <p class="fs-5"><a class="text-black" href="{{ educator.url | relative_url }}">{{ educator.givenName }} {{ educator.familyName }}</a></p>
    <img class="educator"
         witdth="80"
         height="80"
         src="{{ educator.thumbnail }}"
         alt="{{ educator.givenName }} {{ educator.familyName }}" />
    <p><em>{{ educator.description }}</em></p>
  </article>
{% endfor %}
</div>
