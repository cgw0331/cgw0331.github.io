---
layout: default
title: 한국어
permalink: /ko/
nav: true
nav_order: 7
description: 강원대학교 의생명과학연구실(BDS Lab) 박사과정.
---

{% include home_style.liquid %}

<div class="home" lang="ko">
<div class="home-hero">
<div class="h-eyebrow">박사과정 · 의생명과학연구실 (BDS Lab)</div>
<h1>GeonWoo <span>Choi</span></h1>
<p class="h-lead">🚧 제작 중입니다.</p>
<div class="h-actions">
<a class="h-btn primary" href="{{ '/projects/' | relative_url }}"><i class="fa-solid fa-flask"></i> 프로젝트</a>
<a class="h-btn" href="{{ '/blog/' | relative_url }}"><i class="fa-solid fa-pen-nib"></i> 블로그</a>
<a class="h-btn" href="https://github.com/cgw0331" target="_blank" rel="noopener"><i class="fa-brands fa-github"></i> GitHub</a>
<a class="h-btn" href="{{ '/' | relative_url }}"><i class="fa-solid fa-language"></i> English</a>
</div>
</div>

<section>
<h2 class="h-label">연구 관심사</h2>
<div class="h-grid">
<div class="h-card"><div class="h-icon"><i class="fa-solid fa-atom"></i></div><h3>분자 생성</h3><p>신약 후보를 새로 설계하는 생성 모델과, 잠재 공간에서의 다중 목적 최적화.</p></div>
<div class="h-card"><div class="h-icon"><i class="fa-solid fa-vial"></i></div><h3>ADMET · 독성 예측</h3><p>약물 후보의 흡수, 분포, 대사, 배설, 독성을 예측하는 모델.</p></div>
<div class="h-card"><div class="h-icon"><i class="fa-solid fa-diagram-project"></i></div><h3>의생명 분야 LLM</h3><p>의생명 지식을 바탕으로 추론하는 검색 증강 생성(RAG)과 에이전트.</p></div>
</div>
</section>

<section>
<h2 class="h-label">학력</h2>
<ul class="h-timeline">
<li class="now"><div class="h-when">2025 – 현재</div><h3><a href="/phd/">박사과정, 데이터사이언스학과</a></h3><p>강원대학교 · 의생명과학연구실 (Biomedical Data Science Lab)</p></li>
<li><div class="h-when">2023 – 2025</div><h3><a href="/ms/">석사</a></h3><p>강원대학교 · 의생명과학연구실 (Biomedical Data Science Lab)</p></li>
<li><div class="h-when">2019 – 2023</div><h3><a href="/bs/">학사, 컴퓨터정보통신공학전공</a></h3><p>강원대학교 IT대학 컴퓨터학부</p></li>
</ul>
</section>

<section>
<h2 class="h-label">최근 글</h2>
{% if site.posts.size > 0 %}
<ul class="h-posts">
{% for post in site.posts limit: 5 %}
<li><time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%Y-%m-%d" }}</time><a href="{{ post.url | relative_url }}">{{ post.title }}</a></li>
{% endfor %}
</ul>
{% else %}
<p class="h-empty">아직 글이 없습니다.</p>
{% endif %}
</section>
</div>
