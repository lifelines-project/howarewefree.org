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

  {% assign featured = site.works | where: 'featured','true' | sort: 'featured_order' %}

  {% for work in featured %}

  <div class="carousel-item {% if forloop.first == true %}active{% endif %}">
  <img class="d-block mx-auto" src="{{ work.image | prepend: '/assets/images/' | prepend: site.asset_subpath }}" alt="First slide">

  <div class="carousel-caption d-none d-md-block">

    {% assign c = site.data.contributors.collaborators[work.contributors][0] %}
    {% assign a = site.data.contributors.collaborators[work.contributors][1] %}
    {% assign url = c | downcase | replace: " ","-" | lstrip | prepend: '/' %}
    {% assign url = url | relative_url %}

    {% if work.excerpt.size > 1 %}

      {% unless work.show_collaborators %}
        {% capture collaborator_a %} &nbsp;&nbsp;–<a href="{{ url }}">{{ site.data.contributors.info[c].name }}</a>{% endcapture %}
        {{ work.excerpt | append: collaborator_a | markdownify }}
      {% else %}
        {{ work.excerpt | markdownify }}
      {% endunless %}
    {% endif %}

    {% if work.excerpt.size > 1 %}
      {% if work.show_collaborators %}
        <a href="{{ url }}">{{  site.data.contributors.info[c].name | upcase }} &amp; {{  site.data.contributors.info[a].name | upcase }}</a>
      {% endif %}
    {% else %}
        <a href="{{ url }}">{{  site.data.contributors.info[c].name | upcase }} &amp; {{  site.data.contributors.info[a].name | upcase }}</a>
    {% endif %}

  </div>

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
