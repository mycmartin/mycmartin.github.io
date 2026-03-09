---
layout: archive
title: "论文"
permalink: /zh/publications/
author_profile: true
lang: zh
locale: zh-CN
lang_ref: publications
---

{% if site.author.googlescholar %}
  <div class="wordwrap">你也可以在 <a href="{{site.author.googlescholar}}">我的 Google Scholar</a> 查看论文列表。</div>
{% endif %}

{% include base_path %}
{% assign filtered_pubs = site.publications | where: "lang", page.lang %}

{% if filtered_pubs.size == 0 %}
<p>论文列表整理中。</p>
{% endif %}

{% if site.publication_category %}
  {% for category in site.publication_category  %}
    {% assign title_shown = false %}
    {% for post in filtered_pubs reversed %}
      {% if post.category != category[0] %}
        {% continue %}
      {% endif %}
      {% unless title_shown %}
        <h2>{{ category[1].title }}</h2><hr />
        {% assign title_shown = true %}
      {% endunless %}
      {% include archive-single.html %}
    {% endfor %}
  {% endfor %}
{% else %}
  {% for post in filtered_pubs reversed %}
    {% include archive-single.html %}
  {% endfor %}
{% endif %}
