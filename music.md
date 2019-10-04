---
layout: music
title: Welcome to my music word!
---
## Musicss

  {% for mu in site.music %}
<div>
    <p id="post_title">{{ mu.title }}</p>
    <p>{{ mu.label }} | {{ mu.path }}</p>
    <p>{{ mu.url }}</p>
</div>
<hr />
  {% endfor %}
