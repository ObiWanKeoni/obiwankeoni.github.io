---
layout: page
title: Blog
permalink: /blog/
has_children: true
has_toc: false
---

{%- assign blog_posts = site[page.collection]
 | default: site.html_pages
 | where: "parent", page.title
 | sort: "date" | reverse -%}


# Blog

How to guides and disjointed thoughts on varying topics.
{: .fs-6 .fw-300 }

<ul>
{% for post in blog_posts %}
 <li class="blog mb-6"> 
   <img src="{{ post.image_link }}" alt="{{ post.title }}" class="card-image">
   <div class="card-body">
	   <span class="fs-3">
	   {{ post.date }} 
	   </span>
	   <h3 class="mt-0 mb-0">
	   {{ post.title }}
	   </h3>
	  <p class="mb-2">
	  {{ post.description }}
	  </p>
	   <span class="fs-4">
	   <a href= "{{ post.url }}">Read More<i class="lni lni-arrow-right fs-2"></i></a>
	   </span>
   </div>
</li>
{% endfor %}
</ul>