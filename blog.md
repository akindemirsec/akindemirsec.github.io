---
layout: default
title: Blog
permalink: /blog/
---

<div class="blog-header fu">
  <div>
    <div class="sec-label">// BLOG</div>
    <h1 class="big-heading">Writeups &amp; Notes</h1>
  </div>
  <div class="blog-header-right">
    CTF walkthroughs, memory forensics analysis, DevSecOps guides, and technical notes from security operations.
  </div>
</div>

<div class="count-strip">
  <span>{{ site.posts.size }} POSTS &middot; NEWEST FIRST</span>
  <span>$ ls -lt _posts/</span>
</div>

<div class="fu">
{%- for post in site.posts -%}
  {%- assign idx = forloop.rindex -%}
  <a href="{{ post.url | relative_url }}" class="blog-row">
    <span class="blog-row-idx">{% if idx < 10 %}0{{ idx }}{% else %}{{ idx }}{% endif %}</span>
    <span class="blog-row-date">{{ post.date | date: "%b %-d, %Y" }}</span>
    <span class="blog-row-info">
      <span class="blog-row-title">{{ post.title | escape }}</span>
      {% if post.excerpt %}<span class="blog-row-excerpt">{{ post.excerpt | strip_html | truncatewords: 20 }}</span>{% endif %}
    </span>
    <span class="blog-row-meta">
      {%- if post.categories.size > 0 -%}
        <span class="blog-row-cat">{{ post.categories | first | upcase }}</span>
      {%- endif -%}
      {%- assign words = post.content | number_of_words -%}
      {%- assign mins = words | divided_by: 200 -%}
      {%- if mins < 1 %}{% assign mins = 1 %}{% endif -%}
      <span class="blog-row-time">{{ mins }} MIN READ</span>
    </span>
  </a>
{%- endfor -%}
</div>

{% if site.posts.size == 0 %}
<div class="sec" style="text-align: center; color: var(--text-muted);">
  No posts yet. Check back soon.
</div>
{% endif %}
