---
title: Notes on learning html
date: 2025-11-21
tags: 
---

### 1 HTML 简介

HTML，即超文本标记语言，是构建网页的基础技术，它不是编程语言而是一种定义内容结构的标记语言。使用标签来定义元素，标签通常成对出现，通过属性提供元素的额外信息。

### 2 HTML 结构

#### 2.1 HTML 元素及标签

在 HTML 文档里，标签是构成 HTML 的基本单位。一个标签通常由一对尖括号<>组成。标签有双标签及单标签，在双标签，前一个标签是开始标签，后一个标签是结束标签例如`<p></p>`，其中 p（paragraph 的缩写）就是元素，在 HTML 文档中表示段落的意思。单标签例如`<br>`，`<br>`是换行的意思。

另外在学习和使用 HTML 的过程中，关注每一个标签的语义往往比关注他们在网页上呈现的效果更为重要，因为我们之后会通过 CSS 和 JS 调整网页效果和互动方式。但我们依旧要用规范的 HTML 语言来构建网页的框架，规范化可以提高我们代码的可读性并为我们的日常协作提供便利。

#### 2.2 HTML 基本结构

这是一个 HTML 的基本结构。

```html
 <!DOCTYPE html>
 <html lang="zh-CN">
 <head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
 </head>
 <head>
    <!--采用何种字符编码来解读 HTML 文件-->
    <meta charset="UTF-8">
    <!-- 针对 ie 浏览器的一个兼容性设置 -->
    <meta http-equiv="X-UA-Compatible" content="IE-edge">
    <!-- 针对移动端的设置 -->
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <!-- 配置网页关键字 -->
    <meta name="keywords" content="html，前端">
    <!-- 配置网页描述信息 -->
    <meta name="description" content="本网页是我用来学习 html 的部分笔记">
     <title>my-blog-HTML</title>
    </head>
 </html>
```

**DOCTYPE 声明**

DOCTYPE 声明（文档类型声明）是放在 HTML 文档最顶部的指令，它的核心作用只有一个：告诉浏览器使用哪种文档类型定义来解析和渲染当前页面。

`<!DOCTYPE html>`是 HTML5​ 的文档类型声明，也是所有 HTML 版本中最简单、最简洁的 DOCTYPE 声明。

**head 元素与 body 元素**

`<head>`元素是 HTML 文档的头部，它包含了文档的各种元数据（metadata），如文档的标题、编码、引入的样式表和脚本等。

`<body>`元素包含了 HTML 文档中所有可见的主页面内容，从图片、文本到链接、按钮等，所有用户能看到的元素都被包含在 body 中。

**meta 元数据**

所谓“元数据”，就是关于数据的数据。它并不直接显示在网页页面上给普通用户看，而是给浏览器、搜索引擎和其他网络服务提供关于这个网页的各类关键信息。上面代码的注释体现了`<meta>`的部分作用。

### 3 常用标签

**标题标签**

每个标题独占一行，标题标签无法相互嵌套。

```html
<h1>利用 Swift Playground 学习编程</h1>
```

**段落标签**

`<p>`用于展示段文字。

```html
<p>
  Swift Playground 是一款适用于 iPad 和 Mac 的革命性 App，可以帮助你学习和探索如何使用 Swift 这款强大的语言来编程。App Store 上多款卓越的 App 都是以 Swift 创建的。
</p>
<p>
  Swift Playground 包含了极具吸引力的课程和教程，让你在互动环境中编写真实的 Swift 代码，通过这种方式展示编程和构建 App 的核心概念。
</p>
```

**换行标签**

`<br/>`单标签，用于强制换行。

**文本格式化标签**

```html
<em>iPad 和 Mac</em> 斜体；
<strong>极具吸引力</strong>加粗；
<mark>Swift Playground</mark>高亮；
<code></code>等宽。
```

### 4 盒子标签

`<div></div>`
`<span></span>`

### 5 图像标签

`<img>`在引用图像时有两种路径，分为相对路径和绝对路径，绝对路径又分为本地绝对路径和网络绝对路径。其中可以用 width height 等属性调整图片的宽和高。

`<scr>`是 source 的缩写，它是 HTML 中的一个核心属性，主要用于指定外部资源的位置（URL）。

`<alt>`（全称 alternative text，意为“替代文本”），主要用于为无法显示的资源提供替代说明。

```html
<img width="200" src="./博士帽.jpg" alt="博士">
<img width="200" src="./a/秃了.jpg" alt="秃">
<img width="200" src="../真 Allen.jpg" alt="真">
<a href="../home.html#博士帽">看 home 中的博士帽</a>
<!-- 绝对路径分为两类：本地绝对路径和网络绝对路径 -->
<!-- 本地绝对路径 -->
<img width="200" src="C:\Users\l1585\Pictures\暴富.jpg" alt="暴富">
<!-- 网络绝对路径 -->
<img width="200" src="https://nimg.ws.126.net/?url=http%3A%2F%2Fcms-bucket.ws.126.net%2F2025%2F1113%2F40111c75j00t5nawo001oc000xs00mcc.jpg" alt="111">
```

### 6 超链接标签

`<a>` 标签为超链接标签，href（全称 Hypertext Reference，意为“超文本引用”）。

它是 HTML 中用于建立“关联关系”的核心属性，核心作用是指定目标资源的 URL。

`_self`表示在当前窗口打开，`_blank` 表示在新窗口打开。`#`锚点名称可以跳转锚点。

```html
<p>本页介绍完毕</p>
 <a href="#">回到顶部</a>
 <a href="">刷新页面</a>
 <a href="javascript:alert(111);">点我弹窗</a>
<p>
 <a href="tel:10010">电话联系</a>
 <a href="mailto:1585968126qq.com">邮件联系</a>
 <a href="sms:10086">短信联系</a>
 <a href="https://www.bilibili.com/"target="_blank">跳转 B 站</a>
 <a href="https://www.bilibili.com/"target="_self">跳转 B 站</a>
 <a name="真 Allen"></a>
 <a href="#真 Allen">看真 Allen</a>
</p>
```

### 7 表格标签

`cellspacin` 调整单元格间距，`height` 单元格高度，`align` 水平对齐方，`valign` 垂直对齐方式。`tr` 代表一行，`th` 代表表头单元格，`td` 代表内容单元格。`colspan` 跨列合并，`rowspan` 跨行合并。

```html
<table border="1" cellspacing="0">
    <caption>表格标题</caption>
    <thead>
        <tr>
          <th>表头单元格</th>
          <th colspan="5">上课</th>
          <th colspan="2">活动与休息</th>
        </tr>
    </thead>
    <tbody>
         <tr>
          <td>星期</td>
          <td>星期一</td>
          <td>星期二</td>
          <td>星期三</td>
          <td>星期四</td>
          <td>星期五</td>
          <td>星期六</td>
          <td>星期日</td>
         </tr>
         <tr>
          <td rowspan="4">上午</td>
          <td>3-2</td>
          <td>3-3</td>
          <td>3-4</td>
          <td>3-5</td>
          <td>3-6</td>
          <td>3-7</td>
          <td rowspan="4">3-8</td>
         </tr>
         <tr>
          <td>4-2</td>
          <td>4-3</td>
          <td>4-4</td>
          <td>4-5</td>
          <td>4-6</td>
          <td>4-7</td>
         </tr>
         <tr>
          <td>5-2</td>
          <td>5-3</td>
          <td>5-4</td>
          <td>5-5</td>
          <td>5-6</td>
          <td>5-7</td>
         </tr>
         <tr>
          <td>6-2</td>
          <td>6-3</td>
          <td>6-4</td>
          <td>6-5</td>
          <td>6-6</td>
          <td>6-7</td>
         </tr>
         <tr>
          <td rowspan="2">7-1</td>
          <td>7-2</td>
          <td>7-3</td>
          <td>7-4</td>
          <td>7-5</td>
          <td>7-6</td>
          <td>7-7</td>
          <td rowspan="2">7-8</td>
         </tr>
         <tr>
          <td>8-2</td>
          <td>8-3</td>
          <td>8-4</td>
          <td>8-5</td>
          <td>8-6</td>
          <td>8-7</td>
         </tr>
    </tbody>
    <tfoot></tfoot>
</table>
```

### 8 列表标签

列表分为有序列表 `ol`、无序列表 `ul` 和自定义列表 `dl`

```html
<h2>把大象放进冰箱需要几步</h2>
<ol>
    <li>把冰箱门打开</li>
    <li>把大象放进去</li>
    <li>把冰箱门关上</li>
    <li>
     <a href="https://cn.bing.com/">访问 bing</a>
    </li>
</ol>
    
<h2>最想去的城市</h2>
<ul>
    <li>上海</li>
    <li>成都</li>
    <li>
        <span>青岛
        <ul>
          <li>五四广场</li>
          <li>五四广场</li>
          <li>五四广场</li>
        </ul>
        </span>
    </li>
    <li>镇江</li>
</ul>

<h2>自定义列表：术语名称、术语描述</h2>
    <dl>
      <dt>术语名称</dt>
      <dd>术语描述</dd>
      <dd>术语描述</dd>
      <dt>111</dt>
      <dd>222</dd>
    </dl>
```
### 9 表单标签

```html
<form action="https://search.jd.com/search" method="get" target="_blank">
<!-- 文本输入框 -->
 <fieldset>
     <legend>主要信息</legend>
    <label for="zhanghu">账户：</label>
        <input id="zhanghu" type="text" name="account" value="请输入账户" maxlength="10"><br>
        <!-- 密码输入框 -->
        <label>
        密码：<input type="password" name="password" value="请输入密" maxlength="6">
        </label>
        <br>
        <!-- 单选框 -->
        性别：
        <input type="radio" name="gender" value="male" id="nan">
        <label for="nan">男</label>
        <label>
        <input type="radio" name="gender" value="female" checked>女
    </label>
 </fieldset>
<br>
       <!-- 多选框 -->
 < fieldset>
        <legend>附属信息</legend>
          爱好：
          <label>
            <input type="checkbox" name="hobby" value="read" checked>读书
          </label>
          <label>
            <input type="checkbox" name="hobby" value="travel">旅游
          </label>
          <input type="checkbox" name="hobby" value="sport" id="yundong">
          <label for="yundong">运动</label>
          <br>
          <label for="qita">其他：</label>
          <textarea id="qita" name="other" cols="20" rows="3" ></textarea><br>
          籍贯：
          <select name="place" >
            <option value="冀">河北</option>
            <option value="青">青岛</option>
            <option value="川" selected>成都</option>
          </select>
 </fieldset>

<!-- 隐藏域 -->
<input type="hidden" name="from" value="bing"><br>
    <!-- 确认按钮的写法 -->
    <!-- <button type="submit">确认</button> -->
    <input type="submit" value="确认"><br>
    <!-- 重置按钮的写法 -->
     <button type="reset">重置</button>
     <input type="reset" value="点我重置"><br>
    <!-- 普通按钮 -->
    <button type="button">监测账户是否被注册</button>
    <input type="button" value="监测账户是否被注册">
</form>
  <!-- 禁用表单控件：disabled -->
  <!-- 利用 iframe 嵌入一个普通网页 -->
   <!-- <iframe src="https://www.miyoushe.com/" width="400" height="200" frameborder="1"></iframe><br> -->
    <a href="https://www.miyoushe.com//zzz/" target="container">点我进入绝区零</a><br>

<form action="https://www.miyoushe.com//zzz//search" target="container">
    <input type="text" name="keyword">
    <input type="submit" value="搜索">
</form>

    <iframe name="container" frameborder="0" width="450" height="250"></iframe> 
    
```

### 10 字符实体

```html
<div>我&nbsp;&nbsp;&nbsp;她</div>
<div>&lt;h1&gt;</div>
<div>&amp;nbsp;</div>
<div>￥的字符实体是&amp;yen;</div>
<div>版权所有&amp;copy;</div>
<div>乘号&amp;times; 除号&amp;divide;</div> 
```

### 11 其他

`pre` 按原文显示

```html
<pre>
    I     love     you
      I   love  you
          love
</pre>
```
### 12 H5 新增
```html
headerS
```

### 参考：
https://blog.csdn.net/weixin_35294091/article/details/149681554
https://zhuanlan.zhihu.com/p/1923148557617206321
https://www.bilibili.com/video/BV1p84y1P7Z5/