---
authors: [Ralvine]
title: 数据仓库与治理
# subtitle: 副标题.
date: 2023-10-22T20:20:40+08:00
lastmod: 2023-11-06T20:25:40+08:00
draft: false
description: 
#license: MIT
images: ["https://z1.ax1x.com/2023/10/23/piAtBlV.png"]
#seriesNavigation: 系列导航.
featuredImage: 
featuredImagePreview: "https://z1.ax1x.com/2023/10/23/piAtBlV.png"
hiddenFromHomePage: true
hiddenFromSearch: true
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

## 数仓建设规范[^3]

[^3]: 最强最全面的数仓建设规范指南 @五分钟学大数据 https://yuanmore.blog.csdn.net/article/details/121265222

### 架构原则

#### 数仓分层

1. ODS 源
2. DW 明细 建模
	- DWD (Detail) 清理 规范化
	- DWM (Middle) 聚合 中间表
	- DWS (Service) 汇总 主题域服务数据 宽表（字段多）
3. DM 轻汇总
4. APP 应用
	- 数据产品 数据分析 报表
5. 维表层
	- 高基数：资料表 数据量大
	- 低基数：配置表

#### 主题域划分

{{< mermaid >}}graph LR;
    A[系统A] --> B(业务过程A)
    A[系统A] --> C(业务过程B)
    A[系统A] --> D(业务过程C)
    B --> E{主题域A}
    C --> F{主题域B}
    D --> G{主题域C}
{{< /mermaid >}}

- 数据域：面向业务分析，将业务过程或维度进行抽象的集合。
  - 业务过程：不可拆分的行为事件，可以定义指标，如买家下单事件
  - 维度：度量环境，如买家是维度
  为保障整个体系的生命力，数据域是需要抽象提炼，并且长期维护和更新的，但不轻易变动。在划分数据域时，既能涵盖当前所有的业务需求，又能在新业务进入时无影响地被包含进已有的数据域中和扩展新的数据域。


#### 数据模型设计



普通全量表[^4]

[^4]: 生命周期管理矩阵 https://img-blog.csdnimg.cn/img_convert/d07f7d6509938865ac596bfcfcbee826.png


### 模型

1. 星型模型：事实表+维度表

### 数据倾斜

大量的数据集中到了一台或者几台机器上计算。

表现
- MapReduce：ruduce阶段卡在99.99%
- Spark：个别task执行极慢

分类
- 频率倾斜：某区域数据量过多
- 大小倾斜：部分记录大小过大

## Hadoop


## 实例：尚硅谷-电商数仓[^1][^2]

[^1]: https://www.bilibili.com/video/BV1yY411b72x/?vd_source=e81e93bc6892fd0d7e19b265d26a2b3a

[^2]: 尚硅谷物流数仓笔记（数仓基础知识） @橘生淮南 https://zhuanlan.zhihu.com/p/647035072