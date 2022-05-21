## Updating theme
- git submodule update --remote --merge

## default front matter
\---
title: "{{ replace .Name "-" " " | title }}"
date: {{ .Date }}
draft: true
cover:
    image: 
    alt: 
    relative: true
\---

## tips 
- youtube shortcode: {{< youtube videoid >}}
- refernce page2 inside page1: [film]({{< ref "/film" >}} "films")
    - can use {{< ref "/page2#key1" >}} to reference the key inside another page