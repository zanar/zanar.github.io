---
permalink: /resume/
---

## Resume

- Date of Birth: June 8th, 1985
- Marital Status: Single
- Interests: Technology, Motorbike, Sports

### Experience

-------------------------------

<div>
  {% for post in site.posts %}
    {% if post.category == "exp" %}
      <div style="border-bottom: 1px solid #eee; padding-bottom: 0.3em;">
        <span style="font-weight: bold; font-style: italic;">{{ post.title }}</span><br/>
        {{ post.content }}<br/>
      </div>
    {% endif %}
  {% endfor %}
</div>
