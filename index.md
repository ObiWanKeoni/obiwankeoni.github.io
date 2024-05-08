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

### 👋 Hello there
{: .my-0}

# Keoni Garner
{: .mb-0 .mt-1 .fs-10}

#### Senior Software Engineer @ [ƒabric](https://fabrichealth.com){: style="text-decoration: none;"}
{: .mt-2 .mb-3 }

### About

Initially, software engineering appeared as an elusive ambition to me, seeming too complex, yet it always intrigued me. My journey began unexpectedly in 2016 during my Petroleum Engineering studies, when I encountered a required programming course and chose C++. That experience sparked a profound interest in coding for me.

Pursuing a degree in Computer Science was tempting, but the thought of extending my university education held me back. Instead, I completed my degree at Community College and then eagerly enrolled in a coding bootcamp. Today, I'm a software engineer with a diverse portfolio, contributing meaningful value to a variety of industries through my work.

More importantly, though, I am a father to one wonderful little boy (Dakota 2) and a mediocre husband to my beautiful wife (Jamie 27). My hobbies include ergonomics, keyboards, and [creative writing](/writing/) (mainly Lovecraftian Horror).

Interested in working together? Reach out at my [email](mailto:keoni_garner@yahoo.com)

- - -

### Recent Blog Posts
{: .mt-2 .mb-5}

{% for post in blog_posts limit:3 %}
({{post.date}}) [{{post.title}}]({{post.url}})
{% endfor %}

[All Blog Posts](/blog){: .button}
{: .mt-4 .mx-auto}

- - -

### Experience
{: .mt-2 .mb-5}

{% for child in sorted_pages limit:2 %}

<div class="mb-2" markdown="1">
####  [{{child.title}}]({{child.url}})
{% if child.nav_order == 1 %}
Active
{: .label .label-green .ml-0 .my-0}
{% endif %}
</div>

{% for history in child.history %}
{{ history.dates }}
{: .fs-2 .my-0}

**{{ history.title }}**
{: .my-2}
{% endfor %}

{{ child.content }}

- - -

{% endfor %}

[View Full Résumé](/resume){: .button}
{: .mt-4 .mx-auto}