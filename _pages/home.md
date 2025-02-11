---
permalink: /
title: Welcome to My Portfolio!
layout: archive
sort_by: date
sort_order: reverse
---
This site is still under construction, but it includes what I consider to be my most important recent projects, so please look through it!

{% assign sortedCollections = site.collections | sort: 'index' %}
{% for collection in sortedCollections %}
  {% unless collection.output == false or collection.label == "posts" %}
<h2 class="archive__subtitle">{{ collection.title }}</h2>
    {% assign sortedPosts = collection.docs | sort: 'date' | reverse %}
    {% for post in sortedPosts %}
      {% include archive-single.html type=page.entries_layout %}
    {% endfor %}
  {% endunless %}
{% endfor %}
