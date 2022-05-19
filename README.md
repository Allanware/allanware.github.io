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
- refernce another page: [film]({{< ref "/film" >}} "films")