---
title: node.js 简介与 nvm
date: 2025-12-11
tags: node.js
---
写这篇文章主要是为了记录自己学习 node.js 的过程。

### 什么是 Node.js 

Node.js 是一个开源的、跨平台的 JavaScript 运行时环境，它让开发者能够使用 JavaScript 编写服务器端应用程序。简单来说，它让 JavaScript 从浏览器中"走出来"，可以在服务器上运行。

### 安装 Node.js

访问[Node.js 官方网站](https://nodejs.org/zh-cn)下载安装包，装完成后，打开终端，运行以下命令来验证是否成功：

```bash
node -v
```

注意这个命令可以在任意目录下执行，它会显示当前系统安装的 Node.js 版本。我这里显示的是 v24.11.1。

### 运行第一个 Node.js 程序

下面我们要执行 console.log("Hello World")，这个命令需要在包含 helloworld.js 文件的目录下执行，所以建议专门新建一个 JavaScript 文件夹来存放后续的代码。

```bash
mkdir node-test
cd node-test
echo console.log("Hello World"); > helloworld.js
```

或者先新建 js 文件再手动编辑文件内容

```bash
echo. > helloworld.js
```

然后使用 dir 检查文件是否创建成功，成功的话是可以看到 helloworld.js 文件，查看文件内容是可以输出 console.log("Hello World");的。

```bash
dir
type helloworld.js
```
### Node.js 核心机制

Node.js 的事件驱动和非阻塞 I/O 模型是其高性能的核心机制。

#### 事件驱动

事件驱动暂时不明白，过后再补充吧。

#### 非阻塞 I/O 模型

这里先介绍一下非阻塞 I/O 模型，非阻塞 I/O 是一种编程模型，其中 I/O 操作不会阻塞程序的主执行线程。当一个 I/O 操作被调用时，程序**不会等待**它完成，而是**立即返回**并继续执行后续代码。

```javascript
客户端1请求 → 创建线程1 → 等待I/O（阻塞） → 响应
客户端2请求 → 创建线程2 → 等待I/O（阻塞） → 响应
客户端3请求 → 创建线程3 → 等待I/O（阻塞） → 响应
```
这里的线程是操作系统能够进行运算调度的最小单位，是进程中的实际运作单位。

通俗理解，线程是执行代码的路径，一个进程（程序）至少有一个线程（主线程），线程共享进程的内存空间，每个线程有自己的调用栈和寄存器。

类比经营餐厅，每个客户点完菜（发出请求），都会分配一个服务员（线程），每个服务员全程为同一个客户服务全程（I/O），直到客户离店（响应）。Node.js 就相当于一个高效的服务员（主线程）和多个后厨助手（线程池），服务员接收所有订单，交给后厨，然后立即接待下个客户。

Web 应用中很多的时间在等待 I/O，Node.js 用这些时间服务其他请求。

### 创建第一个 Node.js 程序

**初始化项目**

在终端进入 node-test 文件夹，初始化 npm 项目，会生产一个 package.json 的文件。

```bash
npm init -y
```
![package.json](cb08d68cbe9cb59fe1a76311dddf86ff.png)

**创建主文件**
先创建一个 js 文件

```bash
echo. > first.js
```

输入以下代码

```javascript
const http = require('http');

const server = http.createServer((req, res) => {
  res.statusCode = 200;
  res.setHeader('Content-Type', 'text/plain');
  res.end(' RUNOOB Node Test ~ Hello, Node.js!\n');
});

const port = 3000;
server.listen(port, () => {
  console.log(`服务器运行地址：http://localhost:${port}/`);
});
```

**运行项目**

在终端存放 js 文件夹目录下执行

```javascript
node first.js
```

打开浏览器访问 http://localhost:3000，页面会显示：

**"RUNOOB Node Test ~ Hello, Node.js!**

### nvm
nvm 是 Node Version Manager（Node 版本管理器）的缩写，它是一个用于在同一台机器上管理和切换多个 Node.js 版本的工具。

#### 安装 nvm
我是 win 系统，先进入 github[下载 nvm-windows](https://github.com/coreybutler/nvm-windows/releases)，但是我会跳转到这个界面 https://www.virustotal.com/gui/file/2d5ad523aa6182205da77c0eb8210638aaa8792f4e6a4bc12e1ac854c5455a68?nocache=1，这可能是安全软件过度保护导致的。
9

所以我直接跳转[https://github.com/coreybutler/nvm-windows/releases/download/1.1.11/nvm-setup.exe](https://github.com/coreybutler/nvm-windows/releases/download/1.1.11/nvm-setup.exe)下载成功，按步骤安装。

安装过程中出现一下提醒：
Node v24.11.1 is already installed. Do you want NVM to control thisversion?

我选择 yes，选择 yes 后 nvm 会统一管理所有 Node.js 版本，避免版本冲突。安装完成后，重启终端或者重启电脑，在终端验证 nvm 版本。

```bash
nvm version
```

#### 验证 nvm 和 node.js 安装
我在之前创建的 helloworld.js 文件里输入以下内容：

```bash
console.log('Hello, Node.js!');
console.log('Node.js 版本:', process.version);
console.log('当前工作目录:', process.cwd());
console.log('操作系统:', process.platform);
```
但是出现以下提醒：
D:\work\my-study-notes\node-test>node first.js
'node' 不是内部或外部命令，也不是可运行的程序
或批处理文件。

D:\work\my-study-notes\node-test>nvm list
No installations recognized.

这表明我的的 Node.js 没有正确安装或环境变量有问题。nvm 没有检测到任何 Node.js 安装。我是这么解决的：

```bash
# 安装你之前已有的 v24.11.1
nvm install 24.11.1

# 使用这个版本
nvm use 24.11.1

# 设置为默认版本
nvm alias default 24.11.1
```
然后重新 node helloworld.js，最后输出：
```
Hello, Node.js!
Node.js 版本：v24.11.1
当前工作目录：D:\work\my-study-notes\node-test
操作系统：win32
```
还可以检查全局安装路径

```bash
# 查看 npm 全局包安装路径
npm config get prefix

# 查看 npm 配置
npm config list

# 查看 Node.js 安装路径
which node
# Windows 上使用
where node
```