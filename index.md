---
layout: home
title: My Blog
---
# Welcome to My Blog

Thoughts on AI, Robotics, Technology, and Society.

---

## Latest Articles

{% for post in site.posts %}

### [{{ post.title }}]({{ post.url }})

*{{ post.date | date: "%B %d, %Y" }}*

{{ post.excerpt }}

[Read More]({{ post.url }})

---

{% endfor %}
