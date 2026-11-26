---
layout: default
title: about
permalink: /
description: GeonWoo Choi, Ph.D. student at the Biomedical Data Science Lab, Kangwon National University.
---

{% include home_style.liquid %}

<div class="home">
<div class="home-hero">
<div class="h-eyebrow">Ph.D. student · Biomedical Data Science Lab</div>
<h1>GeonWoo <span>Choi</span></h1>
<p class="h-lead">🚧 This site is under construction.</p>
<div class="h-actions">
<a class="h-btn primary" href="{{ '/projects/' | relative_url }}"><i class="fa-solid fa-flask"></i> Projects</a>
<a class="h-btn" href="{{ '/blog/' | relative_url }}"><i class="fa-solid fa-pen-nib"></i> Blog</a>
<a class="h-btn" href="https://github.com/cgw0331" target="_blank" rel="noopener"><i class="fa-brands fa-github"></i> GitHub</a>
<a class="h-btn" href="{{ '/ko/' | relative_url }}"><i class="fa-solid fa-language"></i> 한국어</a>
</div>
</div>

<section>
<h2 class="h-label">Research interests</h2>
<div class="h-grid">
<div class="h-card"><div class="h-icon"><i class="fa-solid fa-atom"></i></div><h3>Molecular generation</h3><p>Generative models for de novo drug design, and multi-objective optimization in their latent space.</p></div>
<div class="h-card"><div class="h-icon"><i class="fa-solid fa-vial"></i></div><h3>ADMET and toxicity</h3><p>Predicting absorption, distribution, metabolism, excretion and toxicity of drug candidates.</p></div>
<div class="h-card"><div class="h-icon"><i class="fa-solid fa-diagram-project"></i></div><h3>LLMs for biomedicine</h3><p>Retrieval-augmented generation and agents that reason over biomedical knowledge.</p></div>
</div>
</section>

<section>
<h2 class="h-label">Education</h2>
<ul class="h-timeline">
<li class="now"><div class="h-when">2025 – present</div><h3><a href="/phd/">Ph.D. student, Data Science</a></h3><p>Kangwon National University · Biomedical Data Science Lab (BDS Lab)</p></li>
<li><div class="h-when">2023 – 2025</div><h3><a href="/ms/">M.S.</a></h3><p>Kangwon National University · Biomedical Data Science Lab (BDS Lab)</p></li>
<li><div class="h-when">2019 – 2023</div><h3><a href="/bs/">B.S., Computer and Communications Engineering</a></h3><p>Kangwon National University · GPA 4.31 / 4.5</p></li>
</ul>
</section>

<section>
<h2 class="h-label">Selected projects</h2>
<div class="h-grid">
{% assign home_projects = site.projects | sort: "importance" %}
{% for project in home_projects limit: 4 %}
<a class="h-card" href="{{ project.url | relative_url }}"><span class="h-tag">{{ project.category }}</span><h3>{{ project.title }}</h3><p>{{ project.description }}</p></a>
{% endfor %}
</div>
</section>

<section>
<h2 class="h-label">Latest posts</h2>
{% if site.posts.size > 0 %}
<ul class="h-posts">
{% for post in site.posts limit: 5 %}
<li><time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%Y-%m-%d" }}</time><a href="{{ post.url | relative_url }}">{{ post.title }}</a></li>
{% endfor %}
</ul>
{% else %}
<p class="h-empty">Nothing here yet. Posts will show up as I write them.</p>
{% endif %}
</section>
</div>
