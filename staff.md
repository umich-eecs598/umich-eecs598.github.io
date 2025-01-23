---
layout: page
title: Staff
description: A directory of the teaching staff for Deep Learning for Robot Perception at the University of Michigan.
nav_order: 10
---

# Deep Rob Course Staff

---

## Instructors
<div markdown="1" class="staff-column">

{% assign instructors = site.staffers | where: 'role', 'Instructor' |sort: 'order' %}
{% for staffer in instructors %}
{{ staffer }}
{% endfor %}

</div>

## Graduate Student Instructor
<div markdown="1" class="staff-column">

{% assign gsis = site.staffers | where: 'role', 'Graduate Student Instructor' |sort: 'order' %}
{% assign num_gsis = gsis | size %}
{% if num_gsis != 0 %}

{% for staffer in gsis %}
{{ staffer }}
{% endfor %}
{% endif %}

</div>

## Instructional Assistants
<div markdown="1" class="staff-column">

{% assign ias = site.staffers | where: 'role', 'Instructional Assistant' | sort: 'order' %}
{% for staffer in ias %}
{{ staffer }}
{% endfor %}

</div>

## Advising Faculty
<div markdown="1" class="staff-column">

{% assign advising_faculty = site.staffers | where: 'role', 'Advising Faculty' %}
{% assign num_advising_faculty = advising_faculty | size %}
{% if num_advising_faculty != 0 %}

{% for staffer in advising_faculty %}
{{ staffer }}
{% endfor %}
{% endif %}

</div>


# Office Hours Schedule
{: #weekly-schedule }

<div markdown="1" style="max-width: 900px">
{: .highlight }
**The schedule of instructor office hours, including the in-person locations, is provided in the following Google calendar.**
</div>

<div markdown="1" style="max-width: 900px">
{: .note }
**For accessing office hours virtually, please refer to the calendar for each instructor's preferred Zoom link. If no Zoom link is listed, please join their office hours queue and share your personal Zoom link as your location.**
</div>

<iframe src="https://calendar.google.com/calendar/embed?height=600&wkst=1&ctz=America%2FDetroit&showPrint=0&mode=WEEK&src=Y18zZDZhOGMyMTg0Y2I3ZDA4ZmIwZDg4OGM1OWNiNTU0OGViNzczMTZiOTg3ZTE3YmFlYjFkZDkwOWRhZWQyZTc2QGdyb3VwLmNhbGVuZGFyLmdvb2dsZS5jb20&color=%23C0CA33" style="border:solid 1px #777" width="900" height="600" frameborder="0" scrolling="no"></iframe>
