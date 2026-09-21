---
layout: default
title: UTM-генератор
---

{% assign upcoming_events = site.posts | where_exp: "event", "event.date >= site.time" | sort: "date" %}

<div class="form-floating mb-3">
  <input type="text" class="form-control" id="source" placeholder="tg_progmsk" list="source-list">
  <label for="source">utm_source</label>

  <datalist id="source-list">
    <option value="devpraktika.ru">
    <option value="telegram">
    <option value="tg_progmsk">
    <option value="tg_anton0f">
    <option value="vk_progmsk">
    <option value="vk_dp">
    <option value="calendar">
  </datalist>

  <input type="text" class="form-control" id="medium" placeholder="social" list="medium-list">
  <label for="medium">utm_medium</label>

  <datalist id="medium-list">
    <option value="organic">
    <option value="social">
  </datalist>

  <input type="text" class="form-control" id="campaign" placeholder="" list="campaign-list">
  <label for="medium">utm_campaign</label>

  <datalist id="medium-list">
    {% for event in upcoming_events %}
    <option value="event_{{ event.networkly_id }}_announcement">
    {% endfor %}
  </datalist>
</div>
