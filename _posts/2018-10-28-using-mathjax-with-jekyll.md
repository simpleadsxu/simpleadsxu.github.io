---
layout: single
title:  "Using MathJax with Jekyll"
date:   2018-10-28 15:03:38 -0400
author: JS
categories: web
tags:
  - web 
  - MathJax
  - Jekyll
excerpt: Use MathJax with Jekyll to display LaTex.
---

There are quite a lot of articles on how to use MathJax with Jekyll, [for example](https://sort-care.github.io/Latex-on-Blog/) .

The idea is quite simple, need to link somd CDN based Javascripts for MathJax and then it will render math symbols for you, just like \\(\LaTeX \\). 

With Jekyll, you can choose to add a few lines to ``_includes/scripts.html``, as it will be included in the ``_layouts/default.html``, hence almost every page. 

As of October 2018, the line to include is as below. I choose to use ``latest.js`` to keep it up-to-date. Would still suggest to check the [official guide](http://docs.mathjax.org/en/latest/start.html) in case this become out of date in the future.

{% highlight html %}
<script type="text/javascript" async
  src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/latest.js?config=TeX-MML-AM_CHTML">
</script>
{% endhighlight %}

You can also choose to add a flag to turn it on. I added a flag ``mathjax: true`` to ``_config.yml``, and you can extend the ``<script></script>`` to the following

{% highlight html %}
{% raw %}
{% if site.mathjax %}
</script>src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/latest.js?config=TeX-MML-AM_CHTML"><script>
{% endif %}
{% endraw %}
{% endhighlight %}

You are probably good now. For some reason, I stil had some problem with inline formulae. If you are having the same issue, you can either try to use ``\\(...\\)``, or override it with the following. Essentially, it allows ``$...$`` and ``\(...\)`` to be rendered as inline formula.
{% highlight html %}
<script type="text/x-mathjax-config">
MathJax.Hub.Config({
  tex2jax: {inlineMath: [['$','$'], ['\(','\)']]}
});
</script>
{% endhighlight %}

Now you can run jekyll build and check the \\(\LaTeX\\) results. 

