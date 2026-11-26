---
layout: page
title: B.S. · Courses
permalink: /bs/courses/
description: Every course I took as an undergraduate, semester by semester, with grades.
nav: false
---

{% include bs_tabs.liquid active="courses" %}

<style>
  .gpa-band { display: grid; gap: 1rem; grid-template-columns: repeat(auto-fit, minmax(150px, 1fr)); margin-bottom: 2.5rem; }
  .gpa-card { border: 1px solid var(--global-divider-color); border-radius: 16px; padding: 1.1rem 1.2rem; background: var(--global-card-bg-color); }
  .gpa-card .k { display: block; font-size: 0.72rem; font-weight: 700; letter-spacing: 0.12em; text-transform: uppercase; color: var(--global-text-color-light); margin-bottom: 0.35rem; }
  .gpa-card .v { font-size: 1.65rem; font-weight: 800; line-height: 1.1; font-variant-numeric: tabular-nums; }
  .gpa-card .v small { font-size: 0.95rem; font-weight: 500; color: var(--global-text-color-light); }
  .term-card h3 small { font-weight: 600; }
  .term-card h3 small .sep { opacity: 0.45; margin: 0 0.35rem; }
  .term-card li .g { flex: none; width: 2.4rem; text-align: right; font-weight: 700; font-variant-numeric: tabular-nums; color: var(--global-theme-color); }
  .term-card li .g.pass { color: var(--global-text-color-light); font-weight: 600; }
  .grade-note { color: var(--global-text-color-light); font-size: 0.9rem; margin-top: 2rem; }
</style>

<div class="gpa-band">
  <div class="gpa-card"><span class="k">Cumulative GPA</span><span class="v">4.31<small> / 4.5</small></span></div>
  <div class="gpa-card"><span class="k">Credits earned</span><span class="v">131</span></div>
  <div class="gpa-card"><span class="k">Major</span><span class="v" style="font-size:1.05rem;font-weight:700">Computer and Communications Engineering</span></div>
</div>

{% assign years = site.data.bs_courses | group_by: "year" %}
{% for y in years %}
<h2 class="year-label">Year {{ y.name }}</h2>
<div class="term-grid">
{% for term in y.items %}
<div class="term-card">
<h3>{{ term.term }} <small>{{ term.credits }} credits<span class="sep">·</span>GPA {{ term.gpa }}</small></h3>
<ul>
{% for c in term.courses %}
<li><span>{{ c.en }}<span class="ko" lang="ko">{{ c.ko }}</span></span><span class="g {% if c.grade == 'P' %}pass{% endif %}">{{ c.grade }}</span><span class="cr">{{ c.credits }}</span></li>
{% endfor %}
</ul>
</div>
{% endfor %}
</div>
{% endfor %}

<p class="grade-note">Grades are on Kangwon National University's 4.5 scale. <strong>P</strong> marks a pass/fail course (가), which carries credit but is not counted in the GPA.</p>
