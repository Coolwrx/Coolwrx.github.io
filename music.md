---
layout: music
title: Welcome to my music word!
---
## Music

  {% for post in site.albums %}
  
<div>
  <a href="{{ albums.url }}">
    <div>
    <p id="post_title">{{ albums.title }}</p>
    <p id="post_preview">{% if albums.abstract %}{{ albums.abstract }}{% else %}{{ albums.content | strip_html | truncate:200 }}{% endif %}</p>
    </div>
  </a>
  <p id="post_msg">Posted on {{ albums.date | date: "%B %-d, %Y" }}</p>
</div>
<hr />
  {% endfor %}