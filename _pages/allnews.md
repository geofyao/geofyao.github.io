---
title: "News"
layout: textlay
excerpt: "News"
sitemap: false
permalink: /allnews.html
---

# Group News

{% for article in site.data.news %}
<p>{{ article.date }} <br>
{{ article.headline }}</p>
{% endfor %}
