## Welcome to the Python Lab

A blog for learning and practicing the Python Programming Language.

### Contributors

- Gregorio Flores
- Pedro Santana 

<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
    {{ post.excerpt }}
  {% endfor %}
</ul>
