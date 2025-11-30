---
layout: search
title: 便捷的查询
permalink: /index/
---

本界面用于对blog内的文章归档，分类，以便于查询

{% for post in site.posts %}
- [{{ post.title }}]({{ post.url }})
{% endfor %}
