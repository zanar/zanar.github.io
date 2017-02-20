---
permalink: /resume/
---

## Resume

- Date of Birth: June 8th, 1985
- Marital Status: Single
- Interests: Technology, Motorbike, Sports

### Experience

<table>
    {% for xp in site.data.resume.experience %}
	<tr>
	    <td style="font-weight: bold;">
		{% if xp.end != "" %}
		    {{ xp.start }} - {{ xp.end }}  
		{% else %}
		    since {{ xp.start }}  
		{% end %}
	    </td>
	    <td style="font-weight: bold;>{{ xp.job }}</td>
	    <td>{{ xp.where }}</td>
	</tr>
	<tr>
	    <td colspan="3">
		{% for w in xp.works %}
		    {{ w }}<br/>
		{% endfor %}
	    </td>
	</tr>
	<tr>
	    <td colspan="3" style="font-style: italic;">{{ xp.abstract }}</td>
	</tr>
    {% endfor %}
</table>