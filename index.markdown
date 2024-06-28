---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: home
title: "Your awesome title"
---

<div class="home">
  <h1 class="page-heading">{{ page.title }}</h1>
  <ul class="post-list">
    {% for post in site.posts %}
    <li>
      {% include post-summary.html post=post %}
    </li>
    {% endfor %}
  </ul>
  {% include pagination.html %}
</div>

---
