---
layout: page
title: Platforms
---
{
    "categories": [
        {% for category in site.categories %}
        "{{ category | first }}"{% unless forloop.last %},{% endunless %}
        {% endfor %}
    ]
}