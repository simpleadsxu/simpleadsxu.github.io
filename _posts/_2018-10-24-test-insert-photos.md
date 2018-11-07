---
layout: single
title:  "Test"
date:   2018-10-24 15:03:38 -0400
categories: test
author: simples02
tags:
  - test2
gallery:
  - url: https://zenglix.github.io/pics/gallery/yale_lib.jpg
    image_path: https://zenglix.github.io/pics/gallery/yale_lib.jpg
    title: "Harkness Tower"
  - url: https://zenglix.github.io/pics/gallery/eastrock.jpg
    image_path: https://zenglix.github.io/pics/gallery/eastrock.jpg
    title: "Yale Beinecke Rare Book Library"
  - url: https://zenglix.github.io/pics/gallery/bryce.jpg
    image_path: https://zenglix.github.io/pics/gallery/bryce.jpg
    title: "Yale Beinecke Rare"	
  - url: https://zenglix.github.io/pics/gallery/bryce.jpg
    image_path: https://zenglix.github.io/pics/gallery/bryce.jpg
    title: "Yale Beinecke Rare 3"		
---

Testing using some random online photos
{% include gallery caption="**Yale University**" %}


<!---
 ![fdaf](https://zenglix.github.io/pics/gallery/yale_lib.jpg = 300px)
 ![faf](https://zenglix.github.io/pics/gallery/eastrock.jpg)

-->

<ul class="photo-gallery">
  {% for image in page.gallery %}
    <li><img src="{{ image.image_path }}" alt="{{ image.title}}" width="30%"/></li>
  {% endfor %}
</ul>
