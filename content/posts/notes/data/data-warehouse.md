---
authors: [Ralvine]
title: 数据仓库与治理
# subtitle: 副标题.
date: 2023-10-22T20:20:40+08:00
lastmod: 2023-10-22T20:25:40+08:00
draft: false
description: 
#license: MIT
images: ["https://z1.ax1x.com/2023/10/23/piAtBlV.png"]
#seriesNavigation: 系列导航.
featuredImage: 
featuredImagePreview: "https://z1.ax1x.com/2023/10/23/piAtBlV.png"
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
tags: ["产品经理", "数据开发", "数据库"]
categories: ["笔记"]
series: ["数据研发与分析"]
series_weight: 1
---

<!--more-->

## 数据仓库[^1]

### 模型

1. 星型模型：事实表+维度表
![星型模型](https://pic1.zhimg.com/80/v2-3ab86050013d9381c1555482df933f58_1440w.webp)


### 数据倾斜

大量的数据集中到了一台或者几台机器上计算。

表现
- MapReduce：ruduce阶段卡在99.99%
- Spark：个别task执行极慢

分类
- 频率倾斜：某区域数据量过多
- 大小倾斜：部分记录大小过大


## 实例：尚硅谷-电商数仓[^1]

[^1]: https://www.bilibili.com/video/BV1yY411b72x/?vd_source=e81e93bc6892fd0d7e19b265d26a2b3a

[^1]: 尚硅谷物流数仓笔记（数仓基础知识） @橘生淮南 https://zhuanlan.zhihu.com/p/647035072