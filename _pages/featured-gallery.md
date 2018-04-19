---
title: Featured Gallery
layout: default
permalink: /gallery/
class: featured
---

<!-- This page features a full bleed gallery, navigation to the next image and text overlay with pull quotes.

Using Bootstrap 4 Carousel functionality (https://getbootstrap.com/docs/4.1/components/carousel/) -->

<div class="container-fluid">
<div id="carouselExampleControls" class="carousel slide">
  <div class="carousel-inner">

  {% for work in site.works %}

  {% if work.featured == true %}  

  <div class="carousel-item {% if forloop.first == true %}active{% endif %}">
  <img class="d-block w-100" src="{{ work.image | prepend: '/assets/images/' }}" alt="First slide">

  {% if work.excerpt %}
  <div class="carousel-caption d-none d-md-block">
    {{ work.excerpt | markdownify }}
  </div>
  {% endif %}

  </div>

  {% endif %}
  {% endfor %}
  </div>
  <a class="carousel-control-prev" href="#carouselExampleControls" role="button" data-slide="prev">
  <span class="carousel-control-prev-icon" aria-hidden="true"></span>
  <span class="sr-only">Previous</span>
  </a>
  <a class="carousel-control-next" href="#carouselExampleControls" role="button" data-slide="next">
  <span class="carousel-control-next-icon" aria-hidden="true"></span>
  <span class="sr-only">Next</span>
  </a>
</div>
</div>
