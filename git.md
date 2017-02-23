---
permalink: /git/
---

## Git Blog

Just a little help about [Git](https://git-scm.com/) to start well or discover new functionnalities!

--------------------------------
### Basic

<ol>
  {% for post in site.categories.git reversed %}
    {% if post.categories contains 'howto' and post.level == 'basic' %}
      <li><a href="{{ post.url }}">{{ post.title }}</a></li>
    {% endif %}
  {% endfor %}
</ol>

--------------------------------
### Advanced

<ol>
  {% for post in site.categories.git reversed %}
    {% if post.categories contains 'howto' and post.level == 'advanced' %}
      <li><a href="{{ post.url }}">{{ post.title }}</a></li>
    {% endif %}
  {% endfor %}
</ol>

--------------------------------
### Expert

<ol>
  {% for post in site.categories.git reversed %}
    {% if post.categories contains 'howto' and post.level == 'expert' %}
      <li><a href="{{ post.url }}">{{ post.title }}</a></li>
    {% endif %}
  {% endfor %}
</ol>
