---
title: Experience
parent: About
has_children: true
has_toc: false
---
{%- assign child_pages = site[page.collection]
 | default: site.html_pages
 | where: "grand_parent", page.parent -%}

{%- include sorted_pages.html pages = child_pages -%}
# Experience
Software engineer with 5+ years of experience across a wide range of industries. I like to build cool things.
{: .fs-6 .fw-300 }


{% for child in sorted_pages %}
- - -
#### [{{child.title}}<i class="lni lni-arrow-right fs-1"></i>]({{child.url}})
{: .mb-2}

{% for history in child.history %}
**{{ history.title }}** // _{{ history.dates }}_
{% endfor %}

{% for language in child.languages %}
**{{ language }}**
{: .label .label-purple }
{% endfor %}
{% endfor %}
