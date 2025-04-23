---
layout: archive
title: "索引"
permalink: /sitemap/
author_profile: true
---

{% include base_path %}

这里可以查找到这个网站的所有相关信息。这里还有一个 [XML 版本]({{ base_path }}/sitemap.xml) available for digesting as well.

<h2>网页</h2>
{% assign target_pages = "publications.html,talks.html,teaching.html,year-archieve.html,portfolio.html"  | split: "," %}
{% for post in target_pages %}
  {% include archive-single.html %}
{% endfor %}

<h2>帖子</h2>
{% for post in site.posts %}
  {% include archive-single.html %}
{% endfor %}

{% capture written_label %}'None'{% endcapture %}

{% for collection in site.collections %}
{% unless collection.output == false or collection.label == "posts" %}
  {% capture label %}{{ collection.label }}{% endcapture %}
  {% if label != written_label %}
  <h2>{{ label }}</h2>
  {% capture written_label %}{{ label }}{% endcapture %}
  {% endif %}
{% endunless %}
{% for post in collection.docs %}
  {% unless collection.output == false or collection.label == "posts" %}
  {% include archive-single.html %}
  {% endunless %}
{% endfor %}
{% endfor %}
