---
permalink: /git/
---

## Git Blog

Just a little help about [Git](https://git-scm.com/) to start well or discover new functionnalities!
  
> *Note:*  
> I'll just talk about commands, tips, walkthroughs and good practices I know and I'm sure about. You may know more about Git than this blog contains...

  
You will be able find usefull informations in the [Git Manual](https://www.kernel.org/pub/software/scm/git/docs/) or in tutorials on the Web.

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

--------------------------------
### Commands

  {% assign sortedPosts = site.categories.git | sort: 'title' %}
  {% assign def_count = 0%}
  {% for post in sortedPosts %}
    {% if post.categories contains 'cmd' and post.tags contains 'def' %}
      {% assign def_count = def_count | plus: 1 %}
    {% endif %}
  {% endfor %}

  {% assign nb_def = def_count | divided_by: 5 %}
  {% assign tot_def = nb_def | times: 5 %}
  {% if tot_def != def_count %}
    {% assign nb_def = nb_def | plus: 1 %}
  {% endif %}

  {% assign i = 0 %}

<table style="border: 0px solid black;"><tr><td style="background-color: transparent;"><ul>
  {% for post in sortedPosts %}
    {% if post.categories contains 'cmd' and post.tags contains 'def' %}
      <li><a href="{{ post.url }}">{{ post.title }}</a></li>
      {% assign i = i | plus: 1 %}
      {% if i == nb_def %}
	</ul></td><td style="background-color: transparent;"><ul>
	{% assign i = 0 %}
      {% endif %}
    {% endif %}
  {% endfor %}
</ul></td></tr></table>
