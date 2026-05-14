---
layout: default
title: "Ведущие"
---

{% assign sorted_educators = site.educators | sort: "givenName" | sort: "familyName" %}
<ul>
  {% for educator in sorted_educators %}
    <li>
      <a href="{{ educator.url | relative_url }}">
        {{ educator.givenName }} {{ educator.familyName }}
      </a>
    </li>
  {% endfor %}
</ul>