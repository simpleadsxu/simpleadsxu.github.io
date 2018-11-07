---
layout: single
title:  "Using Highcharts on Web"
date:   2018-10-12 15:03:38 -0400
author: JS
categories: web
tags:
  - web 
  - highchart
header:
  teaser: /assets/images/highcharts_logo.jpg
excerpt: Embed Highcharts into webpages.
---

Here is some simply examples of using Highcharts on web.

### Method 1 – embedding

The simplest way is to create your charts on the  [Highcharts Cloud](https://cloud.highcharts.com/).

This is a very convenient. We can upload your plot, finely tune it, and it is ready to export.

To export to WordPress, simply go to Share->Embed, and copy the code to WordPress editor (in “Text” mode). Below shows the result:

<div id="highcharts-ocatefo"><script src="https://cloud.highcharts.com/inject/ocatefo/" defer="defer"></script></div>

-   **Cons**: Very easy to do. Highcharts Cloud allows unlimited storage of charts.
-   **Pros**: It relies on the Highcharts Cloud service, and I am not sure its reliability.

### Method 2 – include as JavaScript

This method is a bit more detailed, with all the original data. You just need to follow the simple examples  [here](https://www.highcharts.com/docs/getting-started/your-first-chart).

To simplify, you will need to copy a few lines of code to the WordPress editor (again in “Text” mode). BTW, seems this one is needed too.


{% highlight ruby %}
<script src=”https://code.jquery.com/jquery-3.1.1.min.js”></script>
{% endhighlight %}

-   **Cons**: A bit complicated to create. There must be a lot of APIs to generate it. Probably need search a bit.
-   **Pros**: You are in total control.