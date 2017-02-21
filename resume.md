---
permalink: /resume/
---

## Resume

-------------------------------

- Date of Birth: June 8th, 1985
- Marital Status: Single
- Interests: Technology, Motorbike, Sports

-------------------------------

[Experience](#experience) - [Education](#education) - [Skills](#skills)

### Experience

-------------------------------

<div>
  {% for post in site.posts %}
    {% if post.category == "exp" %}
      <span style="font-weight: bold;">
      {% if post.end == "" or post.end == nil %}
        since {{ post.start }} >
      {% else %}
        {{ post.start }} - {{ post.end }} >
      {% endif %}
      {{ post.title }} - {{ post.company }} > {{ post.where }}</span><br/>
      {{ post.content }}
    {% endif %}
  {% endfor %}
</div><br/><br/>

### Education

-------------------------------

<div>
  {% for post in site.posts %}
    {% if post.category == "edu" %}
      <span style="font-weight: bold;">{{ post.when }} > {{ post.title }}</span><br/>
      {{ post.content }}
    {% endif %}
  {% endfor %}
</div><br/><br/>

### Skills

-------------------------------

<div>
  {% for post in site.posts %}
    {% if post.category == "skl" %}
      <span style="font-weight: bold;">{{ post.title }}</span><br/>
      {{ post.content }}
    {% endif %}
  {% endfor %}
</div><br/><br/>
