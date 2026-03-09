---
layout: archive
permalink: /zh/year-archive/
title: "博客"
author_profile: true
lang: zh
locale: zh-CN
lang_ref: blog
---

{% include base_path %}
{% capture written_year %}'None'{% endcapture %}
{% assign filtered_posts = site.posts | where: "lang", page.lang %}
{% assign post_fallback = false %}
{% if filtered_posts.size == 0 %}
  {% assign filtered_posts = site.posts | where_exp: "item", "item.lang == nil or item.lang == 'en'" %}
  {% assign post_fallback = true %}
{% endif %}

{% if post_fallback and filtered_posts.size > 0 %}
<p class="archive__notice">当前暂无中文版本，已显示英文内容。</p>
{% endif %}

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
