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

  {% assign featured = site.works | where: 'featured','true' %}

  {% for work in featured %}

  <div class="carousel-item {% if forloop.first == true %}active{% endif %}">
  <img class="d-block mx-auto" src="{{ work.image | prepend: '/assets/images/' }}" alt="First slide">

  {% if work.excerpt %}
  <div class="carousel-caption d-none d-md-block">

    {% assign c = site.data.contributors.collaborators[work.contributors][0] %}
    {% assign a = site.data.contributors.collaborators[work.contributors][1] %}
    {% assign url = c | downcase | replace: " ","-" | lstrip | prepend: '/' %}
    {% assign url = url | relative_url %}
    <a href="{{ url }}"><p>
    {{  site.data.contributors.info[c].name | upcase }} &amp; {{  site.data.contributors.info[a].name | upcase }}
    </p></a>

  </div>
  {% endif %}

  </div>

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
