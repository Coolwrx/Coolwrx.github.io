---
layout: music
title: Welcome to my music word!
---

欢迎关注我的[网易云音乐]("https://music.163.com/#/artist?id=12228621")主页！

<div>
<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width=330 height=450 src="//music.163.com/outchain/player?type=0&id=820432870&auto=0&height=430"></iframe>

<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width=330 height=450 src="//music.163.com/outchain/player?type=4&id=793345643&auto=0&height=430"></iframe>
</div>

## Check out all my music

{% for mu in site.music %}
<div>
  <a href="{{ mu.url }}">
    <div>
    <p id="post_title">{{ mu.title }}</p>
    <p id="post_preview">{% if mu.abstract %}{{ mu.abstract }}{% else %}{{ mu.content | strip_html | truncate:200 }}{% endif %}</p>
    </div>
  </a>
  <p id="post_msg">Posted on {{ mu.date | date: "%B %-d, %Y" }}</p>
</div>
<hr />
 {% endfor %}
