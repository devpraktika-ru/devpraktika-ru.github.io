---
layout: default
title: Архив
---

{% assign outgoing_events = site.posts | where_exp: "event", "event.date < site.time" | sort: "date" | reverse %}

# Архив

{% include events.html events=outgoing_events %}
