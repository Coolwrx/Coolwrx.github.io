---
layout: music
title: Welcome to my music word!
---
## Musiccc

  {% for music in site.collections %}
    {% for doc in music.docs %}
  
<div>

    <p id="post_title">{{ doc.title }}</p>

</div>
<hr />
    {% endfor }
  {% endfor %}