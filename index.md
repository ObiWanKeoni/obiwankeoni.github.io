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

<div class="hero" markdown=1>

# I listen.<br>I understand.<br>I <span class="gradient-text">code</span>.<br>In that order.
{: .mt-0}

</div>

### About

#### Senior Software Engineer @ <a style="text-decoration: none;" href="https://iso.io">iso.io</a>
Bakersfield, CA • Remote
GitHub: <a style="text-decoration: none; font-weight: bold;" href="https://github.com/ObiWanKeoni">@ObiWanKeoni</a>
{: .mt-0 .fs-2}
> ***Ask me about my keyboard***

👋 Hello there, my name is **Keoni Garner**
{: .mb-0}

I am a software engineer with experience across a variety of industries and a proven track record of delivering value to businesses for whom I have worked. Interested in working together? Reach out at my [email](mailto:keoni_garner@yahoo.com)

- - -

### Recent Blog Posts

<ul>
{% for post in blog_posts %}
 <li class="blog mb-6"> 
   <img src="{{ post.image_link }}" alt="{{ post.title }}" class="card-image">
   <div class="card-body">
	   <span class="fs-3">
	   {{ post.date | date_to_string }} 
	   </span>
	   <h3 class="mt-0 mb-2">
	   {{ post.title }}
	   </h3>
	   <span class="fs-4">
	   <a class="button" href= "{{ post.url }}">Read Article</a>
	   </span>
   </div>
</li>
{% endfor %}
</ul>

[All Blog Posts](/blog)
{: .mt-4 .mx-auto}

- - -

### Experience
{: .mt-2}
<div class="card-container-horizontal" markdown=1>
{% for child in sorted_pages %}
<div class="experience card mt-5" markdown=1>

<img class="filter" src="{{ child.image_link }}" alt="{{ child.title }}" />

<div class="blog-title" markdown=1>
### {{child.title}}
{: .mb-2 .mt-0 .flex-grow-1}

{% if child.nav_order == 1 %}
Active
{: .label .label-green .ml-0 .mt-0 .flex-grow-0}
{% endif %}
</div>

{% for history in child.history %}
**{{ history.title }}**
{: .mb-0}

{{ history.dates }}
{: .fs-3 .mt-0 .mb-2}
{% endfor %}

{% for language in child.languages %}
<i class="devicon-{{ language | downcase | replace: 'aws', 'amazonwebservices' | replace: 'c#', 'csharp' | replace: '.net', 'dot-net' | replace: 'mssql', 'microsoftsqlserver' }}-plain-wordmark"></i>
{: .fs-6 .devicon}

[Learn More]({{child.url}}){: .button}
{% endfor %}

</div>
{% endfor %}
</div>
