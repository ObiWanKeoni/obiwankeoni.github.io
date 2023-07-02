---
layout: page
title: Blog
permalink: /blog/
---

# Blog

<section class="posts">
<ul>
{% for post in site.categories.blog %}
<li><a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a></li>
{% endfor %}
</ul>
</section>
