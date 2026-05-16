---
layout: default
title: "Ведущие"
---

{% assign sorted_educators = site.educators | sort: "givenName" | sort: "familyName" %}
<ul>
  {% for educator in sorted_educators %}
    <li>
      <img src="{{ educator.thumbnail}}" alt="{{ educator.givenName }} {{ educator.familyName }}" />
      <a href="{{ educator.url | relative_url }}">
        {{ educator.givenName }} {{ educator.familyName }}
      </a>
      <p><em>{{ educator.description }}</em></p>
    </li>
  {% endfor %}
</ul>