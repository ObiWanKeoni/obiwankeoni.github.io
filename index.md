---
title: About
has_children: true
has_toc: false
---
{%- assign child_pages = site[page.collection]
 | default: site.html_pages
 | where: "parent", page.title
 | where: "grand_parent", page.parent -%}

# <img src="assets/images/logo.png" height="18" > Keoni Garner
Bakersfield, CA • Remote

> Ask me about my keyboard

**Dad**
{: .label .label-blue }

**Husband**
{: .label .label-blue }

**Software Engineer**
{: .label .label-blue }

- [email](mailto:keoni_garner@yahoo.com)
- [github](https://github.com/ObiWanKeoni)
<a href="mailto:keoni_garner@yahoo.com">
  <i class="fa fa-envelope"></i>
</a>

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