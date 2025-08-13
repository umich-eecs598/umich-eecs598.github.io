---
layout: page
title: Home
description: A course covering the necessary background of neural-network-based deep learning for robot perception – building on advancements in computer vision that enable robots to physically manipulate objects. ROB 498-004 and ROB 599-004 at the University of Michigan.
nav_order: 1
permalink: /
---

# EECS 598: Action & Perception
{:.no_toc}

<!-- ## Table of contents
{: .no_toc .text-delta } -->


This course covers the necessary background of neural-network-based deep learning for robot perception – building on advancements in computer vision that enable robots to physically manipulate objects. During the first part of this course, students will learn to implement, train and debug their own neural networks. During the second part of this course, students will explore recent emerging topics in deep learning for robot perception and manipulation. This exploration will include analysis of research publications in the area, building up to reproducing and implementing state-of-the-art deep learning approaches as a final course project.

This course is being offered at [the University of Michigan](https://umich.edu/){: target="_blank" rel="noopener noreferrer"} ([Xiaoxiao Du](https://xiaoxiaodu.net){: target="_blank" rel="noopener noreferrer"}, [Anthony Opipari](https://topipari.com){: target="_blank" rel="noopener noreferrer"}, [Chad Jenkins](https://ocj.name/){: target="_blank" rel="noopener noreferrer"}).


This course builds on and is indebted to these existing courses (as a “star” and a "fork" in the open source sense):
- [University of Michigan - ROB 498-011 / 599-011: Deep Learning for Robot Perception](/w24/){: target="_blank" rel="noopener noreferrer"} instructed by [Xiaoxiao Du](https://xiaoxiaodu.net){: target="_blank" rel="noopener noreferrer"}, [Anthony Opipari](https://topipari.com/){: target="_blank" rel="noopener noreferrer"}, and [Chad Jenkins](https://ocj.name/){: target="_blank" rel="noopener noreferrer"}
- [University of Michigan - ROB 498-002 / 599-009: Deep Learning for Robot Perception](/w23/){: target="_blank" rel="noopener noreferrer"} instructed by [Anthony Opipari](https://topipari.com/){: target="_blank" rel="noopener noreferrer"}, [Chad Jenkins](https://ocj.name/){: target="_blank" rel="noopener noreferrer"}, and [Karthik Desingh](https://karthikdesingh.com/){: target="_blank" rel="noopener noreferrer"}
- [University of Michigan - EECS 498-007 / 598-005: Deep Learning for Computer Vision](https://web.eecs.umich.edu/~justincj/teaching/eecs498/WI2022/){: target="_blank" rel="noopener noreferrer"} instructed by [Justin Johnson](https://web.eecs.umich.edu/~justincj/){: target="_blank" rel="noopener noreferrer"}
- [Stanford - CS231n: Deep Learning for Computer Vision](http://cs231n.stanford.edu/index.html){: target="_blank" rel="noopener noreferrer"} instructed by [Fei-Fei Li](https://profiles.stanford.edu/fei-fei-li){: target="_blank" rel="noopener noreferrer"} and [Andrej Karpathy](https://karpathy.ai/){: target="_blank" rel="noopener noreferrer"}


---


# Instructor
<div markdown="1" class="staff-column">

{% assign instructors = site.staffers | where: 'role', 'Instructor' |sort: 'order' %}
{% for staffer in instructors %}
{{ staffer }}
{% endfor %}

</div>

# Graduate Student Instructor
<div markdown="1" class="staff-column">

{% assign gsis = site.staffers | where: 'role', 'Graduate Student Instructor' |sort: 'order' %}
{% assign num_gsis = gsis | size %}
{% if num_gsis != 0 %}

{% for staffer in gsis %}
{{ staffer }}
{% endfor %}
{% endif %}

</div>

<!-- # Instructional Assistants
<div markdown="1" class="staff-column">

{% assign ias = site.staffers | where: 'role', 'Instructional Assistant' | sort: 'order' %}
{% for staffer in ias %}
{{ staffer }}
{% endfor %}

</div> -->

<!-- # Advising Faculty
<div markdown="1" class="staff-column">

{% assign advising_faculty = site.staffers | where: 'role', 'Advising Faculty' %}
{% assign num_advising_faculty = advising_faculty | size %}
{% if num_advising_faculty != 0 %}

{% for staffer in advising_faculty %}
{{ staffer }}
{% endfor %}
{% endif %}

</div> -->

---

<!-- # Office Hours Schedule
{: #weekly-schedule }

<div markdown="1" style="max-width: 1100px">
{: .highlight }
**The schedule of instructor office hours, including the in-person locations, is provided in the following Google calendar.**
</div>

<div markdown="1" style="max-width: 1100px">
{: .note }
**For accessing office hours virtually, please refer to the calendar for each instructor's preferred Zoom link. If no Zoom link is listed, please join their office hours queue and share your personal Zoom link as your location.**
</div>

<iframe src="https://calendar.google.com/calendar/embed?height=600&wkst=1&ctz=America%2FDetroit&showPrint=0&mode=WEEK&src=Y18zZDZhOGMyMTg0Y2I3ZDA4ZmIwZDg4OGM1OWNiNTU0OGViNzczMTZiOTg3ZTE3YmFlYjFkZDkwOWRhZWQyZTc2QGdyb3VwLmNhbGVuZGFyLmdvb2dsZS5jb20&color=%23C0CA33" style="border:solid 1px #777" width="1100" height="600" frameborder="0" scrolling="no"></iframe> -->
