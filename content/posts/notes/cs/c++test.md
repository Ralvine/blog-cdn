---
authors: [Ralvine]
title: C++笔试
# subtitle:
date: 2023-09-12T20:20:40+08:00
lastmod: 2023-09-12T20:25:40+08:00
draft: false
description: 
#license: MIT
images: ["https://z1.ax1x.com/2023/11/01/pinHqnH.png"]
#seriesNavigation: 系列导航.
featuredImage: "https://z1.ax1x.com/2023/11/01/pinHqnH.png"
#featuredImagePreview: 用在主页预览的文章特色图片.
hiddenFromHomePage: false
hiddenFromSearch: false
lightgallery: true
ruby: true
fraction: true
fontawesome: true
linkToMarkdown: true
rssFullText: true
enableLastMod: true
enableWordCount: true
enableReadingTime: true
tags: ["温铁军", "经济", "政治"]
categories: ["笔记"]
series: ["课程-大四"]
series_weight: 1
---

<!--more-->

- 输入输出
    - 带空格 getline
    - 字符串处理 string
    - 大小写转换
        - string: algorithm transform(str.begin(),str.end(),str.begin(),::tolower);
        - char: -'a'+'A'
    - 进制转换
        - bitset
        - 8(oct), 10(dec), 16(hex), 2(bitset(num))
    - 取整 (int)直接去除小数点后的部分
- 排序 sort 默认升序 自定义规则
    - functional greater<Type>
- 质数 因数分解
    - 时间复杂度 先判断n不是素数再进入计算循环
    - 分解到sqrt(n) 剩下的留n即可