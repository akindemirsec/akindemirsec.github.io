---
layout: default
title: Home
---

<section class="hero fu">
  <div class="hero-left">
    <div class="hero-label">// DFIR & CYBER SECURITY ANALYST</div>
    <div class="hero-name">AKIN<br>DEMIR</div>
    <p class="hero-desc">
      I investigate security incidents, hunt threats, and build forensic analysis workflows. Here I share my CTF writeups, security research, and technical notes.
    </p>
    <div class="hero-badges">
      <span class="hero-badge">DFIR & SECURITY ANALYST</span>
      <span class="hero-badge">FORWARD DEPLOY ENGINEER</span>
    </div>
    <div class="hero-ctas">
      <a href="{{ '/blog/' | relative_url }}" class="btn-accent">READ THE BLOG &rarr;</a>
      <a href="{{ '/about/' | relative_url }}" class="btn-outline">ABOUT ME &rarr;</a>
    </div>
  </div>
  <div class="hero-right">
    <div class="avatar-frame">
      <img src="{{ '/akn-avatar.png' | relative_url }}" alt="Akin Demir">
      <div class="avatar-corner-bl"></div>
      <div class="avatar-corner-br"></div>
    </div>
  </div>
</section>

<div class="status-strip fu">
  <div class="status-strip-left">
    <span><span class="pulse-dot"></span> AVAILABLE FOR DFIR ENGAGEMENTS</span>
    <span>LOC: TURKEY (UTC+3)</span>
  </div>
  <span>{{ site.email }}</span>
</div>

<section class="sec fu">
  <div class="sec-head">
    <span class="sec-head-tag">[ SKILLS ]</span>
    <span class="sec-head-right">03 DOMAINS</span>
  </div>
  <div class="skills-grid">
    <div class="skills-col">
      <div class="skills-col-head">01 SECURITY</div>
      <div class="skill-item"><span class="tree">&boxur;</span> SIEM / SOC</div>
      <div class="skill-item"><span class="tree">&boxur;</span> Incident Response</div>
      <div class="skill-item"><span class="tree">&boxur;</span> Memory Forensics</div>
      <div class="skill-item"><span class="tree">&boxur;</span> Malware Analysis</div>
      <div class="skill-item"><span class="tree">&boxur;</span> Threat Hunting</div>
      <div class="skill-item"><span class="tree">&boxur;</span> Volatility</div>
      <div class="skill-item"><span class="tree">&boxur;</span> Binalyze AIR</div>
    </div>
    <div class="skills-col">
      <div class="skills-col-head">02 DEVELOPMENT</div>
      <div class="skill-item"><span class="tree">&boxur;</span> Python</div>
      <div class="skill-item"><span class="tree">&boxur;</span> Django</div>
      <div class="skill-item"><span class="tree">&boxur;</span> React</div>
      <div class="skill-item"><span class="tree">&boxur;</span> React Native</div>
      <div class="skill-item"><span class="tree">&boxur;</span> Java</div>
      <div class="skill-item"><span class="tree">&boxur;</span> Swift / iOS</div>
      <div class="skill-item"><span class="tree">&boxur;</span> Android</div>
    </div>
    <div class="skills-col">
      <div class="skills-col-head">03 INFRASTRUCTURE</div>
      <div class="skill-item"><span class="tree">&boxur;</span> Docker</div>
      <div class="skill-item"><span class="tree">&boxur;</span> Linux</div>
      <div class="skill-item"><span class="tree">&boxur;</span> DevSecOps</div>
      <div class="skill-item"><span class="tree">&boxur;</span> Jenkins</div>
      <div class="skill-item"><span class="tree">&boxur;</span> PostgreSQL</div>
      <div class="skill-item"><span class="tree">&boxur;</span> MySQL</div>
    </div>
  </div>
</section>

<section class="sec fu">
  <div class="sec-head">
    <span class="sec-head-tag">[ LATEST WRITEUPS ]</span>
    <span class="sec-head-right"><a href="{{ '/blog/' | relative_url }}">VIEW ALL &rarr;</a></span>
  </div>
  {%- for post in site.posts limit: 5 -%}
  <a href="{{ post.url | relative_url }}" class="post-row">
    <span class="post-row-date">{{ post.date | date: "%b %-d, %Y" }}</span>
    <span class="post-row-title">{{ post.title | escape }}</span>
    {%- if post.categories.size > 0 -%}
      <span class="post-row-cat">{{ post.categories | first | upcase }}</span>
    {%- else -%}
      <span></span>
    {%- endif -%}
  </a>
  {%- endfor -%}
</section>

<section class="cta-grid fu" style="border-bottom: 1px solid var(--border);">
  <a href="{{ '/projects/' | relative_url }}" class="cta-card">
    <div class="cta-card-num">01 / SELECTED WORK</div>
    <div class="cta-card-title">Projects</div>
    <span class="cta-card-link">Projects &rarr;</span>
  </a>
  <a href="{{ '/contact/' | relative_url }}" class="cta-card">
    <div class="cta-card-num">02 / GET IN TOUCH</div>
    <div class="cta-card-title">Contact</div>
    <span class="cta-card-link">Contact &rarr;</span>
  </a>
</section>
