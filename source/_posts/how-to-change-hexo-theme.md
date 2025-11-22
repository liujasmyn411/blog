---
title: 如何更改 Hexo 博客的主题
date: 2025-11-22 20:55:42
tags: hexo
---

最近我用 Hexo 框架构建了博客，想为博客更改一个主题，此贴是为了记录我更改主题的过程和过程中遇到的问题。

### 选择主题

首先可以在[Hexo 官方主题界面](https://hexo.io/themes/)选择自己喜欢的主题，当然有其他途径也可以。我选择是 [redefine 主题](https://redefine.ohevan.com/)，并找到主题的配置文件：https://github.com/EvanNotFound/hexo-theme-redefine。以下所有步骤都以 redefine 为例。

### 安装 Redefine 主题

有两种安装方法，首先进入自己的博客根目录。用 npm 或 git 方式安装主题到自己的根目录。

```bash
cd blog
# 安装Redefine主题
npm install hexo-theme-redefine
```
或者
```bash
git clone https://github.com/EvanNotFound/hexo-theme-redefine.git
```

### 修改主题配置

编辑自己根目录下的 _config.yml 文件，找到 theme 选项并修改为：

```yaml
theme: redefine
```

### 复制主题配置文件

复制主题的默认配置文件到博客根目录

```bash
cp node_modules/hexo-theme-redefine/_config.yml _config.redefine.yml
```

注意：

1. `cp`是 Unix/Linux 类操作系统​下的复制命令，如果你的电脑是 windows，请将`cp`更换为`copy`。

2. Windows 中路径分隔符应该使用反斜杠\而不是正斜杠/，请按照自己的操作系统合理更改命令。 

3. 如果这个时候提示是否要覆盖_config.yml 文件，请选择否。如果点击了是请按照以下的步骤恢复：

**检查 Git 历史恢复**

```bash
# 查看文件变更
git status

# 如果文件在Git中，尝试恢复
git checkout HEAD -- _config.yml
```

完成恢复命令后，重新复制主题配置文件。                            

### 自定义主题配置

可以借鉴下列的配置，将主题更改为自己喜欢的样子。

```yaml
# 基本信息配置
site:
  title: "你的博客标题"
  subtitle: "博客副标题"
  description: "博客描述"
  author: "你的名字"
  avatar: "/images/avatar.jpg"  # 头像图片路径

# 导航菜单配置
menu:
  Home: /
  Archives: /archives
  Tags: /tags
  Categories: /categories
  About: /about

# 主题样式配置
style:
  primary_color: "#3b82f6"  # 主色调
  dark_mode: true  # 启用暗色模式
```

### 创建并编辑必要的页面

创建三个必要的界面
```bash
# 创建标签页
hexo new page tags

# 创建分类页
hexo new page categories

# 创建关于页
hexo new page about
```

编辑刚创建的页面文件，一般都在 source 文件夹下。

```yml source/tags/index.md
---
title: 标签
type: tags
layout: tags
---
```

```yml source/categories/index.md
---
title: 分类
type: categories
layout: categories
---
```


```yml source/about/index.md
---
title: 关于
layout: about
---
```

### 测试主题效果
`hexo server`后，可以访问链接进行预览，我是这个预览链接：http://localhost:400。

预览完毕后可以随时按 Ctrl+c 终止预览，终止后不会影响最终主题构建效果。
```bash
# 清理缓存
hexo clean

# 生成静态文件
hexo generate

# 启动本地服务器预览
hexo server
```

### 部署到 GitHub

```bash
hexo deploy
```
注意：完成以上所有步骤并配置主题成功后，建议将修改提交到 Github。

```bash
git add .
git commit -m "更换Redefine主题"
git push
```
最后，你可以访问自己的博客确认页面状态。

恭喜！你成功学会部署博客主题。