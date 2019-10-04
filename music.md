---
layout: music
title: Welcome to my music word!
---
## Musicss

  {% for mu in site.collections %}
<div>
    <p id="post_title">{{ mu.title }}</p>
    <p>{{ mu.label }} | {{ mu.path }}</p>
</div>
<hr />
  {% endfor %}
