---
authors: [Ralvine]
title: 泛函分析
# subtitle:
date: 2023-03-01T20:20:40+08:00
lastmod: 2023-03-01T20:25:40+08:00
draft: false
description: 22-23 春夏学期「泛函分析」课程学习笔记。
#license: MIT
images: ["https://z1.ax1x.com/2023/10/23/piAW5eH.png"]
#seriesNavigation: 系列导航.
featuredImage: 
featuredImagePreview: "https://z1.ax1x.com/2023/10/23/piAW5eH.png"
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
tags: ["王伟", "数学", "专业必修课"]
categories: ["笔记"]
series: ["本科课程"]
series_weight: 1
---

<!--more-->

{{< admonition quote "课程信息" true >}}
🎓 数学科学学院<br>
🕙 2022-2023 春夏<br>
🧑‍🏫 王伟<br>
📝 20%小测，20%作业，60%期末
{{< /admonition >}}

{{< admonition note "课程材料" true >}}
- 《实变函数与泛函分析概要（第五版）》王声望，郑维行
- 课程讲义
    - Ch1.1
    - Ch1.2
    - Ch2.1
    - Ch2.2
    - Ch3.1
    - Ch3.2
- 泛函分析笔记 @Reichtum
- 课后习题讲解 @Reichtum
    - [度量空间](https://zhuanlan.zhihu.com/p/486354129)
    - [Banach&Hilbert](https://zhuanlan.zhihu.com/p/524355026)
- [*智云课堂回放*](https://classroom.zju.edu.cn/coursedetail?course_id=48021&tenant_code=112)
{{< /admonition >}}


## Ch1. 距离空间

- 定义
    - 距离公理：非负、对称、三角不等式
    - 非空即可定义、不唯一
    - 离散距离空间
    - $\mathbb{R}^n$
        - 欧氏距离、复数域
        - **柯西不等式**
        - max定义
    - 连续函数空间$C[a,b]$
    - $l^p$
        - 元素：无限数列、级数绝对收敛
        - 距离定义
            - Holder不等式
            - **Minkowski不等式**、证明
    - $l^\infty$
    - $L^p(F)$
        - 可测集F
        - 距离定义
            - Holder不等式
            - Minkowski不等式
    - $L^\infty$
        - 本性有界
        - 本性有界可测、几乎处处相等看作同元素
        - 距离定义$essinf_F$
- 收敛
    - 点列收敛
        - 性质：极限唯一、有界
        - 子列收敛
    - 欧式空间$\mathbb{R}^n$的收敛（如何证）
        - 点列收敛、坐标收敛
    - $C[a,b]$ 的收敛
        - 按照距离导出收敛
        - 某距离收敛等价函数列一致收敛
- 点集
    - 开球、闭球
    - 开集、闭包、闭集
    - 内点、内部
    - 聚点、导集、孤立点
    - 稠密性
    - 可分性
        - $L^\infty[a,b]$
- 连续映射
    - 连续性等价条件
    - 归结原则、集合描述
    - 同胚、等距
- 完备性
    - 柯西基本列
    - 完备性
        - 三条定理
        - $C[a,b]$、$l^p$、$L^\infty(F)$ 完备
        - $S$ 三角不等式及**完备性证明**
    - 完备化
        - 完备扩展定理
        - $C[a,b]\rightarrow L^2[a,b]$
        - $P\rightarrow C[a,b]$
- 稀疏集
    - 与球的的充要条件
- 闭球套定理、第一/二类型集
- $l_0^p$
    - 子空间、不完备、稠密
- $S$、$s$、$P$
- 准紧集、紧集、全有界集
    - $\epsilon-$ 网
    - 相互关系
    - 紧集套
    - 开覆盖
    - 有限交
    - 连续映射
- 不动点定理、压缩映射

- **重点梳理**
    - 常见度量空间，及其距离、收敛、可分性、准紧条件
        - $\mathbb{R}^n$ （所有分量收敛）
        - $C[a,b]$（一致收敛）、$C^k[a,b]$、$C^\infty [a,b]$
        - $l^p$、$l^\infty$（不可分）
        - $L^p$、$L^\infty$（不可分）
        - $S$（测度收敛）、$s$（按坐标收敛）
    - 重要证明
        - Cauchy、Holder、Minkowski、Young
    - 各类点集、球、稠密、可分
    - 基本列、收敛、完备
    - 连续映射
    - 不动点、压缩映射


## Ch2. 巴拿赫空间、希尔伯特空间

- 赋范线性空间
    - 距离空间、范数/强收敛
    - Banach
    - 商空间
    - 直和
- 内积空间
    - 导出范数
        - Schwarz不等式、极化恒等式
        - 平行四边形公式
    - $l^2,L^2$
    - 正交、正交补、推广勾股
    - 规范正交系
        - Bessel
        - 完备、完全
        - Schmidt正交化
        - 最佳逼近
- Hilbert
    - 凸集、正交分解
    - E.S.Fischer
    - Parseval
    - 可分同构


## Ch3. 有界线性算子：巴拿赫空间

## Ch4. 有界线性算子：希尔伯特空间

## 参考资料

小测：https://www.cc98.org/topic/5321722