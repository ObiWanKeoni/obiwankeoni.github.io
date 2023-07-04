---
title: About
has_children: true
has_toc: false
---
{%- assign child_pages = site[page.collection]
 | default: site.html_pages
 | where: "parent", page.title
 | where: "grand_parent", page.parent -%}

# Keoni Garner
Bakersfield, CA • Remote

> Ask me about my keyboard

**Dad**
{: .label .label-blue }

**Husband**
{: .label .label-blue }

**Software Engineer**
{: .label .label-blue }

<h3>
<a href="mailto:keoni_garner@yahoo.com">
  <i class="lni lni-envelope"></i>
</a>
<a href="https://github.com/ObiWanKeoni">
  <i class="lni lni-github"></i>
</a>
</h3>

### Experience
{: .text-purple-200 .mt-8}

{% for child in child_pages %}
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