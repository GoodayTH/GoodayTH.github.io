---
title: "page sample"
permalink: /sample/page-sample/ # link 직접 지정
toc: true                       # for Sub-title (On this page)
comments: true                  # for disqus Comments
categories:                     # for categories
date: 2020-03-10 00:00:00 -0000
last_modified_at: 2020-03-25 00:00:00 -0000
sidebar:
  title: "Sample Title"
  nav: sidebar-sample
---

될 수 있은면 이 첫 줄에 페이지 내용을 간결하게 정리하여 적는게 좋다.

## sub title 1

page 123

## sub title 2

page 123 123 12

## link 

* [link](/gitpage-adsense/)

```
[link](/gitpage-adsense/)
```

## edit side bar navigation

```yml
# \data\navigation.yml link

# documentation links
docs:
  - title: Getting Started
    children:
      - title: "Quick-Start Guide"
        url: /docs/quick-start-guide/
      - title: "Structure"
        url: /docs/structure/
      - title: "Installation"
        url: /docs/installation/
      - title: "Upgrading"
        url: /docs/upgrading/
  - title: Customization
    children:
      - title: "Configuration"
        url: /docs/configuration/
      - title: "Overriding Theme Defaults"
        url: /docs/overriding-theme-defaults/
      - title: "Navigation"
        url: /docs/navigation/
      - title: "UI Text"
        url: /docs/ui-text/
      - title: "Authors"
        url: /docs/authors/
      - title: "Layouts"
        url: /docs/layouts/
```

```yml
# _config.yml
    
  # sample page
  - scope:
      path: ""
      type: posts       # 어디폴더 아래있는지 적어야함 (_posts 아래라 posts적음)
    values:
      layout: single
      read_time: false
      author_profile: false
      share: true
      comments: true
      sidebar:
        nav: "sample"
```