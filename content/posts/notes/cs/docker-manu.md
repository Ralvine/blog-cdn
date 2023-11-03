---
authors: [Ralvine]
title: Docker 快速上手手册
# subtitle: 副标题.
date: 2023-10-22T20:20:40+08:00
lastmod: 2023-10-22T20:25:40+08:00
draft: false
description: 文章内容的描述。
#license: MIT
images: ["https://z1.ax1x.com/2023/11/01/pinHjAI.png"]
#seriesNavigation: 系列导航.
featuredImage: "https://z1.ax1x.com/2023/11/01/pinHjAI.png"
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
tags: ["口语", "雅思"]
categories: ["笔记"]
series: ["自我成长"]
series_weight: 1
---

<!--more-->

{% cq %}Docker 是一个应用打包、分发、部署的工具；只虚拟软件需要的运行环境。{% endcq %}


## 简介

### 流程

- **打包**：软件运行所需的依赖、第三方库、软件打包为安装包
- **分发**：将安装包上传到镜像仓库
- **部署**：以命令运行应用，自动模拟运行环境

### 用途

- 开源软件和提供私有部署应用的分发
- 快速测试，免去环境部署过程
- 多个版本共存，不污染系统

## 命令

>`docker ps` 查看当前运行中的容器
>`docker images` 查看镜像列表
>`docker rm container-id` 删除指定 id 的容器
>`docker stop/start container-id` 停止/启动指定 id 的容器
>`docker rmi image-id` 删除指定 id 的镜像
>`docker volume ls` 查看 volume 列表
>`docker network ls` 查看网络列表

## 构建镜像

## 目录挂载

- 使用 Docker 运行后，我们改了项目代码不会立刻生效，需要重新`build`和`run`，很是麻烦。
- 容器里面产生的数据，例如 log 文件，数据库备份文件，容器删除后就丢失了。

> `volume` 由容器创建和管理，创建在宿主机，所以删除容器不会丢失，官方推荐，更高效，Linux 文件系统，适合存储数据库数据。可挂到多个容器上
>
> `tmpfs mount` 适合存储临时文件，存宿主机内存中。不可多容器共享。

## 多容器通信

## Docker-Compose

## 部署

## 备份 迁移

-----

**参考文档**

【1】[上手教程](https://www.bilibili.com/video/BV11L411g7U1)｜01/25

【2】[快速入门文档](https://docker.easydoc.net/doc/81170005/cCewZWoN/lTKfePfP)｜01/25
