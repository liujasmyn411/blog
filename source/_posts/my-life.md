---
title: Node.js
date: 2025-12-
tags: js
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

打开浏览器访问 http://localhost:3000，页面会显示 "RUNOOB Node Test ~ Hello, Node.js!"





