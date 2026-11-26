---
layout: page
title: B.S. · Courses
permalink: /bs/courses/
description: Courses I took as an undergraduate, semester by semester.
nav: false
---

{% include bs_tabs.liquid active="courses" %}

{% assign years = site.data.bs_courses | group_by: "year" %}
{% for y in years %}
<h2 class="year-label">Year {{ y.name }}</h2>
<div class="term-grid">
{% for term in y.items %}
{% assign total = 0 %}
{% for c in term.courses %}{% assign total = total | plus: c.credits %}{% endfor %}
<div class="term-card">
<h3>{{ term.term }} <small>{{ total }} credits</small></h3>
<ul>
{% for c in term.courses %}
<li><span>{{ c.en }}<span class="ko" lang="ko">{{ c.ko }}</span></span><span class="cr">{{ c.credits }}</span></li>
{% endfor %}
</ul>
</div>
{% endfor %}
</div>
{% endfor %}
