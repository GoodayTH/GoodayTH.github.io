---
title: "Github io : sitemap 넣기"
permalink: /github-io/insert-sitemap/                # link 직접 지정
toc: true                       # for Sub-title (On this page)
comments: true                  # for disqus Comments
categories:                     # for categories
date: 2020-05-05 00:00:00 -0000
last_modified_at: 2020-05-05 00:00:00 -0000
sidebar:
  title: "etc"
  nav: etc
sitemap :
  changefreq : daily
  priority : 1.0
---

* [참고사이트](http://jinyongjeong.github.io/2017/01/13/blog_make_searched/)

아마도 이것을 안넣으면 Google Search Console에서 색인지정이 안되는 것으로 보인다.;;; 매우 심각;;

---

/root 밑에 sitemap.xml을 만들어 아래를 넣는다.

```xml
---
layout: null
---
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://www.sitemaps.org/schemas/sitemap/0.9 http://www.sitemaps.org/schemas/sitemap/0.9/sitemap.xsd" xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
  {% for post in site.posts %}
    <url>
      <loc>{{ site.url }}{{ post.url }}</loc>
      {% if post.lastmod == null %}
        <lastmod>{{ post.date | date_to_xmlschema }}</lastmod>
      {% else %}
        <lastmod>{{ post.lastmod | date_to_xmlschema }}</lastmod>
      {% endif %}

      {% if post.sitemap.changefreq == null %}
        <changefreq>weekly</changefreq>
      {% else %}
        <changefreq>{{ post.sitemap.changefreq }}</changefreq>
      {% endif %}

      {% if post.sitemap.priority == null %}
          <priority>0.5</priority>
      {% else %}
        <priority>{{ post.sitemap.priority }}</priority>
      {% endif %}

    </url>
  {% endfor %}
</urlset>
```