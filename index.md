
<script>
  window.MathJax = {
    tex: {
      inlineMath: [['$', '$'], ['\\(', '\\)']]
    }
  };
</script>

<script async
  src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js">
</script>




## Articles

{% for Article in site.posts %}
- [{{ Article.title }}]({{ Article.url | relative_url }})
  
{% endfor %}
