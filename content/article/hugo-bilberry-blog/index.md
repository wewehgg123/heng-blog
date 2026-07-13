---
title: "使用 Hugo + Bilberry 搭建个人博客"
date: 2026-07-10T10:30:00+08:00
draft: false

categories: ["技术"]
tags: ["Hugo", "博客", "GitHub Pages", "静态网站"]
toc: true
author: "Heng"

featuredImage: ""
---

Hugo 是目前最快的静态站点生成器，配合 Bilberry 主题和 GitHub Pages，可以在几分钟内搭建一个美观、高效的个人博客。本文记录完整的搭建过程。

<!--more-->

## 为什么选 Hugo

Hugo 由 Go 语言编写，构建速度极快——即使是上千篇文章也能在毫秒级完成构建。对比 Jekyll、Hexo 等同类工具，Hugo 有以下优势：

- **零依赖**：单个二进制文件，无需安装 Node.js、Ruby 等运行时
- **构建极速**：几百篇文章不到 1 秒完成构建
- **模板强大**：Go template 语法灵活，支持 partials、shortcodes
- **生态丰富**：数百个开源主题可直接使用

## 为什么选 Bilberry 主题

[Bilberry](https://github.com/Lednerb/bilberry-hugo-theme) 是一个功能丰富的 Hugo 主题：

- 支持多种文章类型：文章、图片集、音频、视频、链接、引用
- 内置 Algolia 搜索
- 多语言支持
- Font Awesome 图标
- 响应式设计
- 深色模式

## 部署到 GitHub Pages

使用 GitHub Actions 可以实现推送即部署：

```yaml
name: Deploy Hugo to GitHub Pages
on:
  push:
    branches: [main]
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: peaceiris/actions-hugo@v3
      - run: hugo --minify
      - uses: peaceiris/actions-gh-pages@v4
```

更多细节请参考[官方文档](https://gohugo.io/hosting-and-deployment/hosting-on-github/)。
