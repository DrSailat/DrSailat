---
layout: default
title: Dr. Saira Latif's Blog
description: AI, Robotics, Technology, Well-being
---

# Dr. Saira Latif's Blog

Welcome to my space where I explore **AI, Robotics, Technology, and Well-being**.

---

## ✨ Featured Areas

- 🤖 Artificial Intelligence & Machine Learning  
- 🦾 Robotics & Autonomous Systems  
- 🧠 Human-centered AI  
- 🌿 Well-being & Technology balance  

---

## 📚 Latest Articles

{% for post in site.posts %}
- [{{ post.title }}]({{ post.url | relative_url }})
{% endfor %}

---

## 📊 About This Blog

This blog shares research insights, engineering perspectives, and reflections on intelligent systems and human well-being.

---

<!-- MathJax support -->
<script>
  window.MathJax = {
    tex: {
      inlineMath: [['$', '$'], ['\\(', '\\)']]
    }
  };
</script>

<script async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"></script>
