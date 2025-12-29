---
title: 杂学篇 1！
date: 2025-12-29
tags: sundry-learning
excerpt: 第一篇！每天的学习很多时候会干一些乱七八糟的东西，这些东西之间可能并没有太多关联，可能是自己感兴趣就多看的多了些，也有的是无意中查到的。类似的这些内容就写在这个系列里吧。
---
### 1 curl
今天接触到了 curl 这个命令。
初步的作用是这样的：
```bash
curl https://www.youdao.com/
```
执行后你会得到有道首页的源码，类似这样：

<img src="/blog//images/sundry-1-1.png" title="sundry-1-1" width="600px"/>

curl 是一个用于传输数据的命令行工具，这上面我举例的命令里 curl 的作用是：
1. 发送请求
向有道的主页发送 HTTP/HTTPS 请求
2. 显示响应内容
默认情况下，curl 会将服务器返回的 HTML 源代码​ 输出到终端。例如，你会看到有道主页的 HTML 结构，但不会像浏览器那样渲染页面。
3. 测试连接或调试
常用于检查网站是否可访问、查看响应头、测试 API 接口等。

但是呢我想
```bash
curl https://www.google.com
```
就没有任何返回，我尝试为 curl 设置代理，没有成功。

记录几个关于 curl 常用的命令：
```bash
curl -I https://www.google.com # 只显示 HTTP 响应头
curl -o google.html https://www.google.com # 将输出保存到文件
```
### 2 excerpt
起因是我发现我的博客预览界面是未加任何处理的 markdown 内容，看上去非常杂乱，比如：
<img src="/blog//images/sundry-1-2.png" title="sundry-1-2" width="600px"/>

所以我想写摘要，让它只在预览界面出现，在正文不出现。弄了半天，发现在文档的最前面加入 excerpt 就可以，比如：
<img src="/blog//images/sundry-1-3.png" title="sundry-1-3" width="600px"/>

但是 ai 让我修改主题的列表页模板，我找不到模板在哪里，气得我把 blog 文件夹的文件结构分析了一遍：
- blog：可能是旧的博客备份或测试目录
- node_modules：Node.js 依赖包
- public：Hexo 生成的静态网站文件，hexo g 生成
- 源文件目录 scaffolds：文章模板，里面暂时没什么内容
- 源文件目录 sourc：存放博客的源文件，我自己写的博客里的内容都在这里，包括文本和图片。
- themes：存放主题文件，但是目录为空，因为主题通过 npm 安装，位于 node_modules
- _config.yml：Hexo 主配置文件
- _config.redefine.yml：redefine 是我现在博客主题的配置文件
- _config.landscape.yml：Landscape 主题的配置文件，最一开始的主题
- package.json：Node.js 项目的配置文件，定义项目元数据、依赖和脚本。
- package-lock.json：锁定依赖版本，确保安装一致性
- db.json：Hexo 的数据库文件，存储站点数据
- README.md：项目说明文档
- git：可能是 Git 相关文件或目录，目前为空。
明天再分析的详细一些吧。

### 3 Miscellaneous
对了，为了给杂学篇起一个英文名，学会了一个新的英文单词：Miscellaneous，意思是（人，物）混杂的，各种各样的；多方面的，多才多艺的，但是太长了，最后选择 sundry learning 作为杂学篇的英文名。