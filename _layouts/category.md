{% for post in site.posts %}
    {% if post.category == page.slug %}
- [{{post.title}}]({{post.baseurl}})
    {% endif %}
{% endfor %}
