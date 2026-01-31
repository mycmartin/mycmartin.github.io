---
layout: archive
permalink: /zh/year-archive/
title: "??"
author_profile: true
lang: zh
locale: zh-CN
lang_ref: blog
---

{% include base_path %}
{% capture written_year %}'None'{% endcapture %}
{% assign filtered_posts = site.posts | where: "lang", page.lang %}
{% if filtered_posts.size == 0 %}
<p>暂无博客文章。</p>
{% endif %}
{% for post in filtered_posts %}
  {% capture year %}{{ post.date | date: '%Y' }}{% endcapture %}
  {% if year != written_year %}
    <h2 id="{{ year | slugify }}" class="archive__subtitle">{{ year }}</h2>
    {% capture written_year %}{{ year }}{% endcapture %}
  {% endif %}
  {% include archive-single.html %}
{% endfor %}
