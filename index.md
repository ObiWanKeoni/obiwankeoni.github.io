---
title: Disjointed Thoughts
---


### me
- [email](mailto:keoni_garner@yahoo.com)
- [github](https://github.com/ObiWanKeoni)


	- dad
	- husband
	- software engineer
	- ergonomic keyboard nut

### Notes
- [Radius Search for Scrappy Startup Engineers]()

### Blog
 - [TDB](https://m.youtube.com/watch?v=gAGVAVxUgkc)

### Writing
- [2023-06-30-the-weapon-of-waupun](2023-06-30-the-weapon-of-waupun.md)

<div id="archives">
{% for category in site.categories %}
  <div class="archive-group">
    {% capture category_name %}{{ category | first }}{% endcapture %}
    <div id="#{{ category_name | slugize }}"></div>
    <p></p>

    <h3 class="category-head">{{ category_name }}</h3>
    <a name="{{ category_name | slugize }}"></a>
    {% for post in site.categories[category_name] %}
    <article class="archive-item">
      <h4><a href="{{ site.baseurl }}{{ post.url }}">{{post.title}}</a></h4>
    </article>
    {% endfor %}
  </div>
{% endfor %}
</div>