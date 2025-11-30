---
layout: default
title: "便捷的查询"
permalink: /index/
---

本界面用于对blog内的文章归档，分类，以便于查询

<style>
.post-item {
  margin-bottom: 20px;
  padding: 15px;
  border-bottom: 1px solid #e5e5e5;
}
.post-title {
  font-size: 20px;
  font-weight: bold;
}
.post-date {
  color: #888;
  font-size: 14px;
}
.post-excerpt {
  margin-top: 8px;
  color: #555;
}
</style>

<h1>📚 所有文章</h1>

{% for post in site.posts %}
<div class="post-item">
  <div class="post-title"><a href="{{ post.url }}">{{ post.title }}</a></div>
  <div class="post-date">{{ post.date | date: "%Y-%m-%d" }}</div>
  <div class="post-excerpt">
    {{ post.excerpt | strip_html | truncate: 120 }}
  </div>
</div>
{% endfor %}

