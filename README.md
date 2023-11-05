## Updating theme
- git submodule update --remote --merge

## tips 
- youtube shortcode: `{{< youtube videoid >}}`
- bilibili shortcode: `{{< bilibili bv-id >}}`
    - 如果视频包含多p，则可以在第二个参数设定包含第几p: {{< bilibili BV1TJ411C7An 3 >}}
- music shortcode: see [here](https://hugoloveit.com/zh-cn/theme-documentation-music-shortcode/) and [here](https://github.com/metowolf/MetingJS)
    - example:
        - `{{< music url="test.ogg" cover="test.jpeg" name="musicianName">}}`
    - 仅支持本地 audio， 以及中国各大音乐平台（不支持spotify, apple music，sound cloud）
        - 但spotify, apple music 都在 share下有 copy embed code这个选项，然后直接把code copy到markdown 里就好了

- refernce page2 inside page1: [page2]({{< ref "/page2" >}})
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
    - to enable this layout, set `hybrid: true` in the front matter of an _index.md or _index.zh.md file.