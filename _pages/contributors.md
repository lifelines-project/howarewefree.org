---
title: Contributors
layout: default
permalink: /contributors/
class: default
---

<div class="container">

    <div class="row p-2 border contributors">

    {% for curr in site.data.contributors.info %}

    {% assign info = curr[1] %}

    {% include contributors-grid.html c = info %}
    
    {% endfor %}
    </div>
</div>
