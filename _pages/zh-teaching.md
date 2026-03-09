---
layout: archive
title: "教学"
permalink: /zh/teaching/
author_profile: true
lang: zh
locale: zh-CN
lang_ref: teaching
---

{% include base_path %}

{% assign filtered_teaching = site.teaching | where: "lang", page.lang %}
{% assign teaching_fallback = false %}
{% if filtered_teaching.size == 0 %}
  {% assign filtered_teaching = site.teaching | where_exp: "item", "item.lang == nil or item.lang == 'en'" %}
  {% assign teaching_fallback = true %}
{% endif %}

{% if teaching_fallback and filtered_teaching.size > 0 %}
<p class="archive__notice">当前暂无中文版本，已显示英文内容。</p>
{% endif %}

{% if filtered_teaching.size == 0 %}
<p>暂无教学内容。</p>
{% endif %}
{% for post in filtered_teaching reversed %}
  {% include archive-single.html %}
{% endfor %}
