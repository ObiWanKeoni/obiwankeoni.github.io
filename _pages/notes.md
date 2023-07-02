---
layout: page
title: Notes
permalink: /notes/
---

# Notes

<section class="posts">
<ul>
{% for post in site.categories.notes %}
<li><a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a></li>
{% endfor %}
</ul>
</section>
