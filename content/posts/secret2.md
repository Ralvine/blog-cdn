---
title: 语法笔记
date: 2022-01-12 21:51:35
tags: 
 - Markdown
 - python
---

{% cq %}这是居中引用{% endcq %}

<!-- more-->

```
{% btn url, text, icon [class], [title] %}

url     : Absolute or relative path to URL.
text    : Button text. Required if no icon specified.
icon    : Font Awesome icon name (without 'fa-' at the begining). Required if no text specified.
[class] : Font Awesome class(es): fa-fw | fa-lg | fa-2x | fa-3x | fa-4x | fa-5x
          Optional parameter.
[title] : Tooltip at mouseover.
          Optional parameter.
```

{% btn #, Text %} {% btn #, Text & Title,, Title %}

```
{% label [class]@Text %}

[class] : default | primary | success | info | warning | danger.
          '@Text' can be specified with or without space
          E.g. 'success @text' similar to 'success@text'.
          If not specified, default class will be selected.
```

Lorem {% label @ipsum %} {% label primary@dolor sit %} amet, consectetur {% label success@adipiscing elit, %} sed {% label info@do eiusmod %} tempor incididunt ut labore et dolore magna aliqua.

Ut enim *{% label warning @ad %}* minim veniam, quis **{% label danger@nostrud %}** exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.

Duis aute irure dolor in reprehenderit in voluptate ~~{% label default @velit %}~~ <mark>esse</mark> cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.



{% note info %}
**Welcome** to [Hexo!](https://hexo.io)
{% endnote %}



{% note primary This is a summary %}
Note with summary: `note primary This is a summary`
{% endnote %}



{% tabs Second unique name, 3 %}
<!-- tab -->
**This is Tab 1.**
<!-- endtab -->

<!-- tab -->
**This is Tab 2.**
<!-- endtab -->

<!-- tab -->
**This is Tab 3.**
<!-- endtab -->
{% endtabs %}
