---
title: About
has_children: true
has_toc: false
---
{%- assign child_pages = site[page.collection]
 | default: site.html_pages
 || where: "grand_parent", page.title -%}

{%- include sorted_pages.html pages = child_pages -%}

# ObiWanKeoni
Bakersfield, CA • Remote

***Ask me about my keyboard***

**Dad**
{: .label .label-blue }

**Husband**
{: .label .label-blue }

**Software Engineer**
{: .label .label-blue }


<a href="https://github.com/ObiWanKeoni">
  <i class="lni lni-github fs-7 d-inline-block"></i>
</a>
<a href="mailto:keoni_garner@yahoo.com">
  <i class="lni lni-envelope fs-7 d-inline-block"></i>
</a>

## Experience
{: .mt-10}

{% for child in sorted_pages %}
- - -
#### [{{child.title}}]({{child.url}})
{: .mb-2}

{% for history in child.history %}
**{{ history.title }}** // _{{ history.dates }}_
{% endfor %}

{% for language in child.languages %}
**{{ language }}**
{: .label .label-purple }
{% endfor %}
{% endfor %}