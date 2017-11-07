---
title: Phyton Labs
layout: default
description: A blog for learning and practicing the Python Programming Language.
---

## Welcome to Phyton Labs

A blog for learning and practicing the Python Programming Language.

### Contributors

- Gregorio Flores
- Pedro Santana 

<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>
