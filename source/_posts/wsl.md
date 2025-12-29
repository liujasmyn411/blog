---
title: wsl
date: 2025-12-27
tags: wsl, node
---
本来想在 win 上运行一个 Next.js 文件，但遇到了 Node.js 原生模块（lightningcss）的兼容性问题，没有运行成功，所以想采用 wsl 方案。
###  WSL 是什么
WSL（Windows Subsystem for Linux）是微软在 Windows 10 和 Windows 11 操作系统中内置的 Linux 兼容层，它允许用户在 Windows 系统上直接运行 Linux 二进制可执行文件，而无需安装虚拟机或双系统。

可以在 Windows 终端中**直接运行 Linux 命令和工具**。

WSL 有两种版本：WSL1 与 WSL2。WSL2 在性能、兼容性和功能完整性方面都优于 WSL1，是当前推荐的默认选择。

### 安装 WSL
#### 确认两个前提
1. CPU 虚拟化
打开任务管理器 - 性能 - CPU，在这个页面通常会显示虚拟化已启用，如果还未开启，则需要进入 BIOS 修改一下 BIOS 设置。
2. Windows 功能开启
在任务栏搜索启用或关闭 Windows 功能，找到‘适用于 Linux 的 Windows 子系统’和‘虚拟机平台’点击确定。
第二步完成后需要重启电脑。

#### 安装
在搜索栏中搜索 cmd，以管理员身份运行，输入以下命令，系统或自动下载 Ubuntu，Ubuntu 是 Linux 发行版。
```bash
wsl --install
```
下载完成后，可能要求你重启电脑，按要求照做就好啦。
之后 cmd 提示你输入一个 username 和 password，输入 password 时是不显示密码的。
WSL 支持安装其他的 Linux 发行版：
```bash
wsl --list --online # 展现所有能安装的发行版
wsl --install kali-linux # kali-linux是其中一个发行版
```

### WSL 的启动与停止
安装后之后打开终端：
```bash
wsl --list -v # 展现电脑上所有已安装的Linux子系统
wsl --set-default kali-linux # 切换默认的Linux子系统
```
想使用 wsl 直接在命令行输入 wsl 就可以进入，输入 exit 退出。

### 运行项目
先进入项目目录，我是拿到的 node.js 的压缩包，我直接把解压后的文件夹复制到了 Linux 下。
<img src="/blog/images/wsl1.png" title="wsl" width="600px"/>

```bash
npm install
npm run dev
```
运行以下命令，这会在本地启动一个开发服务器。

### 在 WSL 下安装 git

```bash
sudo apt update # 更新包列表
sudo apt install git # sudo apt install git
git --version # 验证安装
```

### 参考：
[https://www.bilibili.com/video/BV1tW42197za/](https://www.bilibili.com/video/BV1tW42197za/)
[在 Linux 安装 node](https://www.luofenming.com/show.aspx?id=2024060909442174)
