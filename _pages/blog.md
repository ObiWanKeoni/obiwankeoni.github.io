---
layout: page
title: Blog
permalink: /blog/
---

<section class="posts">
<ul>
{% for post in site.posts %}
{{ post.category }}
{{ page.slug }}
{% if post.category == page.slug %}
<li><a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a><time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%m-%d-%Y" }}</time></li>
{% endif %}
{% endfor %}
</ul>
</section>