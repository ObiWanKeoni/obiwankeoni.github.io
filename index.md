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

#### Senior Software Engineer @ [iso.io](https://iso.io){: style="text-decoration: none;"}
{: .mt-2 .mb-3 }

### About

I always thought software engineering was out of reach, that I was simply too dumb to learn it even though it pulled at me subtly. Back in 2016, the curriculum for a Petroleum Engineering degree required a programming course. I chose C++ and **fell in love** with code.

I would have pursued a CS degree if I wouldn't have had to retake a year at University so I finished my Community College degree and jumped headfirst into a coding bootcamp. Now I am a software engineer with experience across a variety of industries and a proven track record of delivering value to businesses for whom I have worked.

More importantly, though, I am a father to one wonderful little boy (Dakota 2) and a mediocre husband to my beautiful wife (Jamie 26). My hobbies include ergonomics, keyboards, and [creative writing](/writing/) (mainly Lovecraftian Horror).

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