---
title: how-to-run-nodejs-items
date: 2025-12-26
tags: 
---
今天尝试运行了一个 node.js 项目，记录一下运行的过程和遇到的问题。

这个项目 Next.js​ 项目，并且使用了 TypeScript。运行它需要遵循 Node.js/TypeScript 项目的标准流程。
### 准备环境
1. Node.js
首先要确保安装 Node.js，不确定是否安装的可以在命令行中运行以下命令来检查。具体安装方法见 [node.js 简介与 nvm](https://liujasmyn411.github.io/blog/2025/12/11/node.js%20%E4%B8%8E%20nvm/)。
```bash
node -v
npm -v
```
2. 解压项目
将包含项目的 zip 压缩包解压到方便的位置。

### 安装依赖
1. 打开终端进入存放解压文件的根目录，我是
```bash
D:\run\app
```
2. 安装项目所需的包
运行以下命令，它会根据 package.json 文件自动下载所有必需的库（依赖项会安装到 node_modules 文件夹）。一般不会马上安装成功，需要等待几分钟。
```bash
npm install
```
3. 运行项目并访问
运行以下命令，这会在本地启动一个开发服务器，在浏览器中访问终端提示的地址就能看到你的 Next.js 应用了。
```bash
npm run dev
```

***

但是我在 npm run dev 这一步遇到了困难，出现了 Node.js 原生模块（lightningcss）的兼容性问题。

<img src="/blog/images/lightningcss.png" title="lightningcss" width="600px"/>

lightningcss 是一个用 Rust 编写的 CSS 处理工具，在 Windows 上需要编译为 .node 扩展名的原生模块。

可以尝试以下解决方案：
1. 重新安装依赖
```bash
# 1. 停止当前服务（Ctrl+C）
# 2. 删除 node_modules 和 package-lock.json
rmdir /s node_modules
del package-lock.json
# 3. 清理 npm 缓存
npm cache clean --force
# 4. 重新安装
npm install
# 5. 重新启动
npm run dev
```
2. 重新安装 lightningcss
```bash
# 单独重新安装有问题的包
npm rebuild lightningcss
# 或
npm uninstall lightningcss
npm install lightningcss
```
但都不太奏效，所以我尝试 WSL 方案。












