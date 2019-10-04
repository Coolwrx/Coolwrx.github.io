---
layout: music
title: Welcome to my music word!
---
## Musicss

  {% for music in site.collections %}
<div>
    <p id="post_title">{{ music.title }}</p>
    <p>{{ music.label }} | {{ music.path }}</p>
</div>
<hr />
  {% endfor %}