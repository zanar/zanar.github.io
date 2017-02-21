---
permalink: /resume/
---

## Resume

- Date of Birth: June 8th, 1985
- Marital Status: Single
- Interests: Technology, Motorbike, Sports

### Experience

Here is the list of all my professionnal experiences

<div>
  {% for post in site.posts %}
    {% if post.category == "exp" %}
      {{ post.title }}<br/>
    {% endif %}
  {% endfor %}
</div>
