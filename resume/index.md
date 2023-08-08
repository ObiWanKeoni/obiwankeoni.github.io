---
title: Experience
parent: About
permalink: /resume
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

{% if child.nav_order == 1 %}
Active
{: .label .label-green .ml-0 .my-0}
{% endif %}

####  [{{child.title}}]({{child.url}})
{: .mb-2}

{% for history in child.history %}
**{{ history.title }}**
{: .mb-0}

{{ history.dates }}
{: .fs-3 .mt-0 .mb-2}
{% endfor %}

{% for language in child.languages %}
<i class="devicon-{{ language | downcase | replace: 'aws', 'amazonwebservices' | replace: 'c#', 'csharp' | replace: '.net', 'dotnetcore' | replace: 'mssql', 'microsoftsqlserver' }}-plain"></i>{{ language }}
{: .label }
{% endfor %}
{% endfor %}

