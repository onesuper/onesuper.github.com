---
layout: default
title: Dreamsome
---
{% include JB/setup %}

<h2>Recent</h2>

<div class='recent'>
  {% for post in site.posts limit:10 %}
    <div class='post'>
      {{post.date | date: '%Y/%m/%d' }}
      <br><br>
      <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a>
      <hr>
    </div>
  {% endfor %}
</div>

