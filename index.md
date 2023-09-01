---
title: About
has_children: true
has_toc: false
layout: hero
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

# 👋 Hello there, my name is **Keoni Garner**
{: .mb-0}

## Listen, Understand, <span class="gradient-text">Build</span>. In that order.
{: .mt-0 .fs-10}

<div class="orb"></div>
<div class='container'>
  <div class='ring ring1'>
    <div class='ring ring2'>
      <div class='ring ring3'>
        <div class='ring ring4'></div>
      </div>
    </div>
  </div>
</div>
</div>

- - -

### About

#### Senior Software Engineer @ <a style="text-decoration: none;" href="https://iso.io">iso.io</a>
Bakersfield, CA • Remote • <a style="text-decoration: none; font-weight: bold;" href="https://github.com/ObiWanKeoni">GitHub</a>
{: .mt-0 .fs-2}
> ***Ask me about my keyboard***

I am a software engineer with experience across a variety of industries and a proven track record of delivering value to businesses for whom I have worked. Interested in working together? Reach out at my [email](mailto:keoni_garner@yahoo.com)

- - -

### Recent Blog Posts

<div class="card-container-horizontal" markdown=1>
{% for post in blog_posts %}
<div class="experience card mt-5 d-flex" style="flex-direction: column;justify-content: space-between;" markdown=1>

<img class="blog-card-image" src="{{ post.image_link }}" alt="{{ post.title }}" />

<div class="blog-title" markdown=1>
### {{post.title}}
{: .mb-2 .mt-0 .float-left style="width: 50%;"}

{{ post.date | date_to_string }} 
{: .float-right}
</div>

{{post.description}}

[Read Article]({{post.url}}){: .button .float-right}
</div>
{% endfor %}
</div>

[All Blog Posts](/blog)
{: .mt-4 .mx-auto}

- - -

### Experience
{: .mt-2}
<div class="card-container-horizontal" markdown=1>
{% for child in sorted_pages %}
<div class="experience card mt-5 d-flex" style="flex-direction: column;justify-content: space-between;" markdown=1>

<img class="filter" src="{{ child.image_link }}" alt="{{ child.title }}" />

<div class="blog-title" markdown=1>
### {{child.title}}
{: .mb-2 .mt-0 .flex-grow-1}

{% if child.nav_order == 1 %}
Active
{: .label .label-green .ml-0 .mt-0 .abs-top-left}
{% endif %}
</div>

{% for history in child.history %}
<div markdown=1>
**{{ history.title }}**
{: .mt-0 .mb-0 .float-left style="width: 50%;"}

{{ history.dates }}
{: .fs-3 .mt-0 .mb-0 .float-right}
</div>
{% endfor %}

<div class="icon-container" markdown=1>
{% for language in child.languages %}
<i class="devicon-{{ language | downcase | replace: 'aws', 'amazonwebservices' | replace: 'c#', 'csharp' | replace: '.net', 'dot-net' | replace: 'mssql', 'microsoftsqlserver' }}-plain-wordmark"></i>
{: .fs-6 .devicon}
{% endfor %}
</div>

[Learn More]({{child.url}}){: .button .float-right}
</div>
{% endfor %}
</div>
