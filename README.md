## Updating theme
- git submodule update --remote --merge

## default front matter
\---
title: "{{ replace .Name "-" " " | title }}"
date: 
author: Wenxuan Zhao
tags: ['']
summary: 
mathjax: true
cover:
    image: 
    alt: 
    relative: true
\---

## tips 
- youtube shortcode: {{< youtube videoid >}}
- refernce page2 inside page1: [film]({{< ref "/film" >}} "films")
    - can use {{< ref "/page2#key1" >}} to reference the key inside another page

## features 
- mathjax 
    - in post front matter set `mathjax: true`
- lastmod
    - by default use the last modified time recorded by git 

## list & single 
- posts (index.md) are single layout 
- home & about is list layout 
- subdirectories under about (film, music, football, weiqi, book, etc.) are what I called list-single hybrid layout 