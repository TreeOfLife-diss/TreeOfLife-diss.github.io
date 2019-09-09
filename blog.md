---
layout: default
title: Blog
---
<h1>Latest Posts</h1>

<i>Click on the post title to read the full post.</i>

<ul>
  {% for post in site.posts %}
    <li>
      <h2><a href="{{ post.url }}">{{ post.title }}</a></h2>
      <p>{{ post.excerpt }}</p>
    </li>
  {% endfor %}
</ul>
