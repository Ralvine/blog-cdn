---
authors: [Ralvine]
title: 微分方程数值解
# subtitle: 副标题.
date: 2023-03-01T20:20:40+08:00
lastmod: 2023-07-01T20:25:40+08:00
draft: false
description: 22-23 春夏学期「微分方程数值解」课程学习笔记。
#license: MI
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
tags: ["数学", "微分方程", "张庆海", "专业必修课"]
categories: ["笔记"]
series: ["本科课程"]
series_weight: 1
---

<!--more-->

{{< admonition quote "课程信息" true >}}
🎓 数学科学学院<br>
🕙 2022-2023 春夏<br>
🧑‍🏫 张庆海<br>
📝 40%平时，60%期末
{{< /admonition >}}


## 参考

- 教材讲义
- [智云课堂回放](https://classroom.zju.edu.cn/coursedetail?course_id=51564&tenant_code=112)


## (Ch7) BVP-FD

> P60-70 (11)

- 有限差分离散化
- 误差和一致性
- 稳定性、收敛性
    - 范数收敛
    - Green函数
        - 解决方案
- 其他边值条件
- 二维
    - Kronecker乘积
    - 范数收敛性
- 不规则边界、收敛性

## (Ch9) Multigrid

> P80-87 (8)

- 残差方程
- 模型问题
- 算法组成
    - 傅立叶模式
    - 松弛
    - 限制、延拓
    - 双网格矫正
    - 多重网格cycles
- 收敛性分析
    - 代数图
    - FMG最优复杂度

## (Ch11) IVP

> P102-138 (37)

- 数学基础
    - ODE
    - 算子范数
    - 矩阵指数
    - Lipschitz连续条件
    - 解的唯一存在性
    - well-posed 适定性
    - 常系数线性IVPs
- 数值方法
    - 欧拉法
    - 前欧拉
    - 后欧拉
    - 梯形法
    - leapfrog 中点法
    - 截断误差
    - 欧拉法的收敛性
    - 零/绝对稳定性
- 线性多步法
    - 一致性、稳定性
    - 零稳定性
    - 线性差分方程
    - 收敛性
    - 绝对稳定性
- 刚性IVPs
    - 刚度 stiffness
    - A-稳定性
- 单步法
    - 一致性、收敛性
    - 绝对稳定性
    - A-稳定性、L-稳定性
- 龙格库塔法
    - 显式法
    - 必要阶数条件
    - 隐式法
    - Collocation 配点法
    - 实用误差估计、步长控制
    - 一致性、收敛性
    - 绝对稳定性
    - I-稳定性、L-稳定性
    - 收缩性、B-稳定性
    - 代数稳定性

## (Ch12) MOL

> P140-155 (16)

- 热方程
    - 抛物、导出
    - 边值条件、精确解
    - FTCS
    - Crank-Nicolson
    - 精度、一致性
    - 绝对稳定性、Lax-Richtmyer稳定性
    - 收敛性
    - 离散最大值原理
    - 冯诺依曼稳定性
- 平流方程
    - 经典MOL法
        - FTCS
        - leapfrog
        - Lax-Friedrichs
        - Lax-Wendroff
        - upwind
        - Beam-Warming
    - CFL条件
    - 修正方程
    - 冯诺依曼分析

## 作业

- Homework01
- Homework02
- Homework03
- Homework04
- Homework05
- Project01
- Project02
- Project03
- Project04

## 前辈经验

> lz这学期上了**张庆海**老师的微分方程数值解课程，个人认为这门课在数院是一门非常有特点的课，虽说比较硬核但确实能学到许多，于是开个帖写写课程体会（顺便安利一手） 1.理论与实践结合 数院的课大多以理论为导向，这门课是少有的几门理论与实践并重的课程之一。本学期这门课一共有两个编程大作业，都与课上学的算法密不可分。顺带提醒，先确保完全弄明白算法之后再动手coding，否则成吨的bug在等着你...
> 
> 2.注重推证过程 毕竟是数院的课...数值解的理论基础总是要考虑清楚。 理论推导主要以“一致性+稳定性=收敛”为主线，讨论了各种数值算法的表现，并且以此为依据，明确了这些算法各自的应用范围。 建议期末考之前多刷讲义，确保足够熟悉讲义上的结论与证明...期末的题量根本就做不完，lz最后做了的题都只有80分不到
> 
> 这课的主要内容有： ode数值求解 线性pde数值求解的有限差分法 多重网格迭代求解线性方程组 有限体积算法（没考...我也没咋听明白...） 这课应该会在春夏学期开设，欢迎感兴趣的同学选修～