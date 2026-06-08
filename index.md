---
layout: default
title: Dr. Saira Latif's Blog
description: AI, Robotics, Technology, Well-being
---

Welcome to my space where I explore **AI, Robotics, Technology, and Well-being**.

---
## Research Profiles
<div style="display: flex; flex-wrap: wrap; gap: 10px; align-items: center;">
<a href="https://orcid.org/0000-0002-1951-674X" target="_blank">
  <img src="https://img.shields.io/badge/ORCID-Profile-A6CE39?logo=orcid&logoColor=white">
</a>

<a href="https://sciprofiles.com/profile/2448958" target="_blank">
  <img src="https://img.shields.io/badge/SciProfiles-Research_Profile-6C63FF?logo=academia&logoColor=white">
</a>


<a href="https://scholar.google.com/citations?user=H1MNex0AAAAJ&hl=en" target="_blank">
  <img src="https://img.shields.io/badge/Google%20Scholar-Profile-4285F4?logo=google-scholar&logoColor=white">
</a>

<a href="linkedin.com/in/dr-s-73b540255" target="_blank">
  <img src="https://img.shields.io/badge/LinkedIn-Profile-0A66C2?logo=linkedin&logoColor=white">
</a>




## 📚 Latest Articles

{% for post in site.posts %}
- [{{ post.title }}]({{ post.url | relative_url }})
{% endfor %}





---

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
