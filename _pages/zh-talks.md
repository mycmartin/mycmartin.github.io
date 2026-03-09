---
layout: archive
title: "报告与分享"
permalink: /zh/talks/
author_profile: true
lang: zh
locale: zh-CN
lang_ref: talks
---

{% if site.talkmap_link == true %}

<p style="text-decoration:underline;"><a href="/talkmap.html">查看演讲地点地图</a></p>

{% endif %}

{% assign filtered_talks = site.talks | where: "lang", page.lang %}
{% assign talks_fallback = false %}
{% if filtered_talks.size == 0 %}
  {% assign filtered_talks = site.talks | where_exp: "item", "item.lang == nil or item.lang == 'en'" %}
  {% assign talks_fallback = true %}
{% endif %}

{% if talks_fallback and filtered_talks.size > 0 %}
<p class="archive__notice">当前暂无中文版本，已显示英文内容。</p>
{% endif %}

{% if filtered_talks.size == 0 %}
<p>暂无报告内容。</p>
{% endif %}
{% for post in filtered_talks reversed %}
  {% include archive-single-talk.html %}
{% endfor %}
