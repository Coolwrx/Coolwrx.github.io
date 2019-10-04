---
layout: music
title: Welcome to my music word!
---
## Musiccc

  {% for music in site.musics %}
<div>
    <p id="post_title">{{ music.title }}</p>
</div>
<hr />
  {% endfor %}