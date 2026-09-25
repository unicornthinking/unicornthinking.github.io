---
layout: default
title: "unicorn의 취향 | 홈"
---

<div id="all-posts">
  <h2>최신 게시글</h2>
  <ul class="post-list">
    {% for post in site.posts %}
      <li class="post-item">
        <span class="post-meta">{{ post.date | date: "%Y-%m-%d" }}</span>
        {% if post.categories.size > 0 %}
          <span class="category-tag">{{ post.categories | join: ", " }}</span>
        {% endif %}
        <h3><a href="{{ post.url | relative_url }}" style="color: #155799; text-decoration: none;">{{ post.title }}</a></h3>
        <p style="color: #555; font-size: 0.95rem;">{{ post.excerpt | strip_html | truncate: 120 }}</p>
      </li>
    {% endfor %}
  </ul>
</div>

<hr style="margin: 3rem 0; border: none; border-top: 1px dashed #ccc;">

<!-- 카테고리별 모아보기 구역 -->
<h2>카테고리별 글 모음</h2>
{% for category in site.categories %}
  {% capture category_name %}{{ category | first }}{% endcapture %}
  <div id="category-{{ category_name | slugify }}" style="margin-top: 2rem; padding-top: 1rem;">
    <h3 style="color: #159957; border-bottom: 1px solid #159957; padding-bottom: 0.3rem;">
      📁 {{ category_name }} <span style="font-size: 0.9rem; font-weight: normal; color: #666;">({{ category[1].size }}개)</span>
    </h3>
    <ul class="post-list">
      {% for post in category[1] %}
        <li class="post-item">
          <span class="post-meta">{{ post.date | date: "%Y-%m-%d" }}</span>
          <a href="{{ post.url | relative_url }}" style="color: #333; font-weight: bold; margin-left: 0.5rem; text-decoration: none;">
            {{ post.title }}
          </a>
        </li>
      {% endfor %}
    </ul>
  </div>
{% endfor %}
