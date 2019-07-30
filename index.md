---
title: Home

---

# Home page

Welcome to the home page.


<div id="recent_post_previews">

  {% for post in site.posts %}
  
<div>
  <a href="{{ post.url }}">
    <div>
    <p id="post_title">{{ post.title }}</p>
    <p id="post_preview">{{ post.content | strip_html | truncate:200 }}</p>
    </div>
  </a>
  <p id="post_msg">Posted on {{ post.date | date: "%B %-d, %Y" }}</p>
</div>
<hr />
  {% endfor %}

</div>