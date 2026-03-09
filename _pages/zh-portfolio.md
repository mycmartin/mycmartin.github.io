---
layout: archive
title: "项目"
permalink: /zh/portfolio/
author_profile: true
lang: zh
locale: zh-CN
lang_ref: portfolio
---

{% include base_path %}

{% assign items = site.portfolio | where: "lang", page.lang %}
{% assign portfolio_fallback = false %}
{% if items.size == 0 %}
  {% assign items = site.portfolio | where_exp: "item", "item.lang == nil or item.lang == 'en'" %}
  {% assign portfolio_fallback = true %}
{% endif %}

{% if portfolio_fallback and items.size > 0 %}
<p class="archive__notice">当前暂无中文版本，已显示英文内容。</p>
{% endif %}

{% for post in items %}
  {% include archive-single.html %}
{% endfor %}
