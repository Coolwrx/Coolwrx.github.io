---
layout: music
title: Welcome to my music word!
---
## Music

  {% for post in site.albums %}
  
<div>
  <a href="{{ album.url }}">
    <div>
    <p id="post_title">{{ album.title }}</p>
    <p id="post_preview">{% if album.abstract %}{{ album.abstract }}{% else %}{{ album.content | strip_html | truncate:200 }}{% endif %}</p>
    </div>
  </a>
  <p id="post_msg">Posted on {{ album.date | date: "%B %-d, %Y" }}</p>
</div>
<hr />
  {% endfor %}