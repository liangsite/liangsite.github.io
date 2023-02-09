---
title: "GolangIDE 无限重置30天试用期"
subtitle: ""
date: 2023-02-05T21:31:36+08:00
draft: false
description: "薅羊毛教程"
tags:
- GolangIDE
categories:
- Go
resources:
- name: "featured-image" 
  src: goland.png
weight: 2
---

白嫖Goland付费软件
<!--more-->


### 背景

- 提升编写代码的舒适度以及开发和书写效率。

### 目的

- 白嫖使用付费的golang编辑器，通过reset插件可以重置golang编辑器的试用时间，从而达到无限免费使用的目的。

### 1、添加插件库
- 打开`GolandIDE`设置
{{< image src="image/settings.png" title="settings" width="300px" height="300px" >}}

- 找到插件Plugins，点击右边小齿轮选择第一个（Manage Plugin Repositories...)
{{< image src="image/plugins.png" title="Plugins" >}}

- 将URL`https://plugins.zhile.io` 添加到仓库列表。
{{< image src="image/url.png" title="url" >}}


### 2、安装插件库
- `Marketplace` 中搜索 reset 插件 => 安装 `IDE EVal Reset`插件，重启IDE即可
{{< image src="image/reset.png" title="reset" >}}


### 3、设置自动刷新试用过期时间策略
- 帮助 => `Eval Reset` => 勾选上 `Auto reset before per restart`
{{< image src="image/autoreset.png" title="auto reset" >}}
