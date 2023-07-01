---
layout: page
title: Writing
permalink: /writing/
---
<section class="posts">
<ul>
{% for post in site.categories.writing %}
<li><a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a></li>
{% endfor %}
</ul>
</section>
