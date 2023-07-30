---
title: About
has_children: true
has_toc: false
---
{%- assign child_pages = site[page.collection]
 | default: site.html_pages
 | where: "grand_parent", page.title -%}
{%- include sorted_pages.html pages = child_pages -%}
{%- assign blog_posts = site[page.collection]
 | default: site.html_pages
 | where: "parent", "Blog"
 | sort: "date" | reverse -%}

# <a style="text-decoration: none;" href="https://github.com/ObiWanKeoni"><i class="lni lni-github gradient-text fs-6"></i>ObiWanKeoni</a>
#### Senior Software Engineer @ <a style="text-decoration: none;" href="https://iso.io">iso.io<i class="lni lni-arrow-top-right"></i></a>
Bakersfield, CA • Remote
> ***Ask me about my keyboard***

**Dad**
{: .label .label-blue }

**Husband**
{: .label .label-blue }

**Software Engineer**
{: .label .label-blue }

### Recent Blog Posts
- - -

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
	   <a href= "{{ post.url }}">Read More<i class="lni lni-arrow-right"></i></a>
	   </span>
   </div>
</li>
{% endfor %}
</ul>

[All Blog Posts<i class="lni lni-arrow-right-circle"></i>](/blog){: .btn .btn-purple .inverse-text}
{: .mt-4 .mx-auto}

- - -

### Experience
{: .mt-2}

{% for child in sorted_pages limit:2 %}

<div class="experience" markdown=1>
 {% if child.nav_order == 1 %}**CURRENT**{: .label .label-green .ml-0}{% endif %}

### [{{child.title}}<i class="lni lni-arrow-right"></i>]({{child.url}})
{: .mb-2}

{% for history in child.history %}
**{{ history.title }}**
{: .mb-0}

{{ history.dates }}
{: .fs-3 .mt-0 .mb-2}
{% endfor %}

{% for language in child.languages %}
<i class="devicon-{{ language | downcase | replace: 'aws', 'amazonwebservices' | replace: 'c#', 'csharp' | replace: '.net', 'dotnetcore' | replace: 'mssql', 'microsoftsqlserver' }}-plain"></i>**{{ language }}**
{: .label }
{% endfor %}

</div>
{% endfor %}

[View Full Résumé<i class="lni lni-arrow-right-circle"></i>](/resume){: .btn .btn-purple .inverse-text}
{: .mt-8 .mx-auto}

