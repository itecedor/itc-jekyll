---
layout: page
title: Portfolio
permalink: /portfolio/
---

{% for project in site.projects reversed %}
  <div class="project">
    <a href="{{ project.url }}">
        <img src="{{ site.baseurl }}/assets/image/{{project.image}}" class="no-border">
        <h3>{{ project.title }}</h3>
    </a>
    <p>{{ project.description }}</p>
  </div>
{% endfor %}

<!-- 
* <a href="https://gothamquilts.com" target="_blank">Gotham Quilts</a>, co-founded and ran for over 10 years, acquired in 2025
* <a href="https://www.etsy.com/shop/Chiagu" target="_blank">Chiagu</a>, founded and ran for 10 years, acquired in 2015 -->