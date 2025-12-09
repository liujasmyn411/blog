---
title: Problems in building a hexo blog
date: 2025-11-16 20:55:42
tags: error
---

# 路径错误

今天尝试用 hexo 生成 blog，在创建过程中出现引用 css 和 js 路径错误的情况。

基本情况如下

blog 网址是：https://liujasmyn411.github.io/blog/
引用的 js 地址是 https://liujasmyn411.github.io/js/jquery-3.6.4.min.js ,但实际地址是 https://liujasmyn411.github.io/blog/js/jquery-3.6.4.min.js

我是这样解决的：

我进入 Hexo 根目录的 `_config.yml`更改了 url 和添加了 root
```yml
url: https://liujasmyn411.github.io
root: /blog
```
