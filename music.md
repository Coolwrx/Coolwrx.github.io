---
layout: music
title: Welcome to my music word!
---
## Musicss

  {% for music in site.collections %}
  {% for mu in music %}
<div>
    <p id="post_title">{{ mu.title }}</p>
    <p>{{ mu.label }} | {{ mu.path }}</p>
</div>
<hr />
  {% endfor %}
  {% endfor %}