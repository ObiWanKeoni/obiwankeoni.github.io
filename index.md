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

# <a style="text-decoration: none;" href="https://github.com/ObiWanKeoni"><i class="lni lni-github fs-6 d-inline-block"></i>ObiWanKeoni</a>
#### Senior Software Engineer @ <a style="text-decoration: none;" href="https://iso.io"><i class="lni lni-arrow-top-right d-inline-block"></i>Isometric Technologies</a>
Bakersfield, CA • Remote
> ***Ask me about my keyboard***


**Dad**
{: .label .label-blue }

**Husband**
{: .label .label-blue }

**Software Engineer**
{: .label .label-blue }

#### Blog Posts
{: .mt-10}

{% for post in blog_posts limit:5 %}
 - [{{ post.title }}]({{ post.url }})
    {{ post.description }}  
{% endfor %}
[View More<i class="lni lni-arrow-right d-inline-block"></i>](blog/index){: .mt-4}

#### Experience
{: .mt-10}

{% for child in sorted_pages limit:2 %}
### [{{child.title}}]({{child.url}})
{: .mb-2}

{% for history in child.history %}
**{{ history.title }}** // _{{ history.dates }}_
{% endfor %}

{% for language in child.languages %}
**{{ language }}**
{: .label .label-purple }
{% endfor %}
{% endfor %}

[View Full Résumé<i class="lni lni-arrow-right d-inline-block"></i>](resume/index){: .mt-8}

