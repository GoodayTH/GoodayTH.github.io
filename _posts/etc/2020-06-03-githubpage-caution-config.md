---
title: "Github Page : _config.yml 수정시 주의사항"
permalink: githubio/caution-config/                # link 직접 지정
toc: true                       # for Sub-title (On this page)
comments: true                  # for disqus Comments
categories:                     # for categories
date: 2020-06-03 00:00:00 -0000
last_modified_at: 2020-06-03 00:00:00 -0000
sidebar:
  title: "etc"
  nav: etc
excerpt: ""
tag:
  - Github Page
category:
  - _config.yml
header:
  teaser: /file/image/etc-page-teaser.gif
---

페이지에 `permalink`를 설정한다면 

```yml
# url마지막에 /을 빼는걸 추천
url                      : "https://8bitscoding.github.io"
```

빼지않으면 sitemap.xml에 /가 두개씩 들어간다.

---

plugins에 `jekyll-sitemap`를 넣었다면 굳이 sitemap.xml을 만들지 않아도 된다.

```yml
# Plugins (previously gems:)
plugins:
  - jekyll-paginate
  - jekyll-sitemap
  - jekyll-gist
  - jekyll-feed
  - jekyll-include-cache
```

---

사이트맵의 크롤링 주기를 직접 넣어준다.

```yml
sitemap :
  changefreq : daily
  priority : 1.0
```