---
title: git-alias
date: 2025-12-27
tags: 前端
tags: git
---
### alias 是什么
介绍一下 git alias 这个 git 命令，简单来说这个命令可以为 git 命令设置最适合你的别名。
比如我们要提交 commit 时通常需要执行以下命令：
```bash
git add .
git commit -m "我是备注"
git push
```
但是利用 alias 命令更改命令别名后可以这样执行：
```bash
git add .
git ci "我是备注"
git push
```
命令是不是简短多了！

下面介绍是怎么实现的。

### 创建并使用别名
```bash
# 1. 创建别名
git config --global alias.st status
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit -m

# 2. 使用别名
git st      # 相当于 git status
git co      # 相当于 git checkout
git br      # 相当于 git branch
git ci "message"  # 相当于 git commit -m "message"
```
可以通过以下命令查看你的所有别名：
```bash
git config --global --get-regexp alias
```
也可以找到 gitconfig 文件里查看别名。位置通常在 C:\Users\用户名\.gitconfig

<img src="/blog/images/alias.png" title="alias" width="600px"/>

类似的你还可以为其他的命令设置别名。

### 创建别名规则
当然别名也不能随意设置，不能与 git 本身冲突，开头不能是短横线（-），最好把原本的命令缩写或者描述命令的功能。
