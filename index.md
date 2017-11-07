## Welcome to Phyton Labs

A blog for learning and practicing the Python Programming Language.

### Contributors

- Gregorio Flores
- Pedro Santana 

<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
      {{ post.excerpt | remove: '<p>' | remove: '</p>' }}
    </li>
  {% endfor %}
</ul>
