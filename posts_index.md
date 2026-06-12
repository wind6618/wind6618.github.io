---
layout: default
title: "便捷的查询"
permalink: /posts_index/
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

<h1>所有文章</h1>
<!-- 搜索框 -->
<input type="text" id="searchInput" placeholder="输入关键词搜索文章..." style="width:50%;padding:8px;margin-bottom:20px;font-size:16px;">

<!-- 文章列表 -->
<div id="postList">
  {% for post in site.posts %}
  <article class="post">
    <header>
      <h2 class="post-title"><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h2>
      <p class="post-meta">{{ post.date | date: "%Y-%m-%d" }}</p>
    </header>
    <div class="post-content">
      {{ post.excerpt | strip_html | truncate: 120 }}
    </div>
  </article>
  {% endfor %}
</div>

<script>
  const searchInput = document.getElementById('searchInput');
  const postList = document.getElementById('postList');
  const posts = postList.getElementsByClassName('post');

  searchInput.addEventListener('input', function() {
    const filter = this.value.toLowerCase();

    for (let i = 0; i < posts.length; i++) {
      const title = posts[i].querySelector('.post-title').innerText.toLowerCase();
      const excerpt = posts[i].querySelector('.post-content').innerText.toLowerCase();

      if (title.includes(filter) || excerpt.includes(filter)) {
        posts[i].style.display = '';
      } else {
        posts[i].style.display = 'none';
      }
    }
  });
</script>
