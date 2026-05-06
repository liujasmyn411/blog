# Git版本管理

# 第1章 Git概述

Git是一个免费的、开源的分布式版本控制系统，可以快速高效地处理从小型到大型的各种项目。

Git易于学习，占地面积小，性能极快。 它具有廉价的本地库，方便的暂存区域和多个工作流分支等特性。其性能优于Subversion(svn)、CVS、Perforce和ClearCase等版本控制工具。

## 1. 何为版本控制

版本控制是一种记录文件内容变化，以便将来查阅特定版本修订情况的系统。

版本控制其实最重要的是可以记录文件修改历史记录，从而让用户能够查看历史版本，方便版本切换。

![img](image\wps1.jpg) 

## 2. 版本控制工具

* **集中式版本控制工具**

CVS、SVN(Subversion)、VSS……

集中化的版本控制系统诸如 CVS、SVN等，都有一个单一的集中管理的服务器，保存所有文件的修订版本，而协同工作的人们都通过客户端连到这台服务器，取出最新的文件或者提交更新。多年以来，这已成为版本控制系统的标准做法。

这种做法带来了许多好处，每个人都可以在一定程度上看到项目中的其他人正在做些什么。而管理员也可以轻松掌控每个开发者的权限，并且管理一个集中化的版本控制系统，要远比在各个客户端上维护本地数据库来得轻松容易。

事分两面，有好有坏。这么做显而易见的缺点是中央服务器的单点故障。如果服务器宕机一小时，那么在这一小时内，谁都无法提交更新，也就无法协同工作。

![img](image\wps3.jpg) 

* **分布式版本控制工具**

Git、Mercurial、Bazaar、Darcs……

像 Git这种分布式版本控制工具，客户端提取的不是最新版本的文件快照，而是把代码仓库完整地镜像下来（本地库）。这样任何一处协同工作用的文件发生故障，事后都可以用其他客户端的本地仓库进行恢复。因为每个客户端的每一次文件提取操作，实际上都是一次对整个文件仓库的完整备份。

分布式的版本控制系统出现之后,解决了集中式版本控制系统的缺陷:

1. 服务器断网的情况下也可以进行开发（因为版本控制是在本地进行的）

2. 每个客户端保存的也都是整个完整的项目（包含历史记录，更加安全）

![img](image\wps4.png) 





## 3. Git和代码托管中心

代码托管中心是基于网络服务器的远程代码仓库，一般我们简单称为远程库。

* **局域网**

GitLab

* **互联网**

GitHub（外网）

Gitee码云（国内网站）

 

# 第2章 Git安装

​		官网地址： https://git-scm.com/或https://github.com/git-for-windows/git/releases 

​		查看GNU协议，可以直接点击下一步。

![img](image\wps7.jpg) 

选择Git安装位置，要求是非中文并且没有空格的目录，然后下一步。

![img](image\wps8.jpg) 

Git选项配置，推荐默认设置，然后下一步。

![img](image\wps9.jpg) 

Git安装目录名，不用修改，直接点击下一步。

![img](image\wps10.jpg) 

Git的默认编辑器，建议使用默认的Vim编辑器，然后点击下一步。

![img](image\wps11.jpg) 

默认分支名设置，选择让Git决定，分支名默认为master，下一步。 

![img](image\wps12.jpg) 

修改Git的环境变量，选第一个，不修改环境变量，只在Git Bash里使用Git。 

![img](image\wps13.jpg) 

选择后台客户端连接协议，选默认值OpenSSL，然后下一步。 

![img](image\wps14.jpg) 

配置Git文件的行末换行符，Windows使用CRLF，Linux使用LF，选择第一个自动转换，然后继续下一步。 

![img](image\wps15.jpg) 

选择Git终端类型，选择默认的Git Bash终端，然后继续下一步。

![img](image\wps16.jpg) 

选择Git pull合并的模式，选择默认，然后下一步。

![img](image\wps17.jpg) 

选择Git的凭据管理器，选择默认的跨平台的凭据管理器，然后下一步。

![img](image\wps18.jpg) 

其他配置，选择默认设置，然后下一步。

![img](image\wps19.jpg) 

实验室功能，技术还不成熟，有已知的bug，不要勾选，然后点击右下角的Install按钮，开始安装Git。

![img](image\wps20.jpg) 

点击Finsh按钮，Git安装成功！

![img](image\wps21.jpg) 

右键任意位置，在右键菜单里选择Git Bash Here即可打开Git Bash命令行终端。

在Git Bash终端里输入git --version查看git版本，如图所示，说明Git安装成功。

![image-20230627170844640](image\image-20230627170844640.png) 

 

# 第3章 Git常用命令

| **命令名称**                         | **作用**       |
| ------------------------------------ | -------------- |
| git config --global user.name 用户名 | 设置用户签名   |
| git config --global user.email 邮箱  | 设置用户邮箱   |
| git init                             | 初始化本地库   |
| git status                           | 查看本地库状态 |
| git add 文件名                       | 添加到暂存区   |
| git commit -m "日志信息" 文件名      | 提交到本地库   |
| git reflog                           | 查看历史记录   |
| git reset --hard 版本号              | 版本穿梭       |

## 1 设置用户签名

### 1.1 基本语法

git config --global user.name 用户名

git config --global user.email 邮箱

### 1.2 案例实操

全局范围的签名设置：

```shell
git config --global user.name yhm
git config --global user.email yaohm7788@163.com
git config --list # 查看全局配置
cat ~/.gitconfig  # cat linux中查看文本的命令  ~ 家 [你当前用户的家]/ .gitconfig
```

说明：

签名的作用是区分不同操作者身份。用户的签名信息在每一个版本的提交信息中能够看到，以此确认本次提交是谁做的。Git首次安装必须设置一下用户签名，否则无法提交代码。

※注意：这里设置用户签名和将来登录GitHub（或其他代码托管中心）的账号没有任何关系。



## **2** **初始化本地库** 

### 2.1 基本语法

**git init**

### 2.2 案例实操

![image-20230627131721466](image\image-20230627131721466.png)

 

## **3** **查看本地库状态**

### 3.1 基本语法

**git status**



### 3.2 案例实操

#### （1）首次查看（工作区没有文件）

![image-20230627132109306](image\image-20230627132109306.png)

#### （2）新增文件

![image-20230627132215734](image\image-20230627132215734.png)

####  （3）再次查看（检测到未追踪文件）

![image-20230627132547573](image\image-20230627132547573.png)



## 4 添加暂存区

### 4.1 将工作区的文件添加到暂存区

#### （1）基本语法

**git** **add** **文件名**

#### （2）案例实操

![image-20230627132954523](image\image-20230627132954523.png)



### 4.2 查看状态（检测到暂存区有新文件）

![image-20230627133040699](image\image-20230627133040699.png)



## 5 提交本地库

### 5.1 暂存区文件提交到本地库

#### （1）基本语法

**git commit -m "日志信息" 文件名**

#### （2）案例实操

![image-20230627133335748](image\image-20230627133335748.png)

### 5.2 查看状态（没有文件需要提交）

![image-20230627133425162](image\image-20230627133425162.png)



## 6 修改文件（hello.txt）

### 6.1 查看状态（检测到工作区有文件被修改）

![image-20230627133644105](image\image-20230627133644105.png)



### 6.2 将修改的文件再次添加暂存区

![image-20230627133907417](image\image-20230627133907417.png)



### 6.3 查看状态（工作区的修改添加到了暂存区）

![image-20230627133937432](image\image-20230627133937432.png)

 

### 6.4 将暂存区文件提交到本地库

![image-20230627134046013](image\image-20230627134046013.png)

## 7  远程关联

### 7.1 连接仓库

**远程仓库url**：

![远程url地址.png](远程url地址.png)

**连接远程仓库**：

```bash
git remote add origin https://gitee.com/liyigiteehao/newtest.git
```

| 参数     | 含义                                                         |
| :------- | :----------------------------------------------------------- |
| `remote` | 管理远程仓库的命令                                           |
| `add`    | 添加一个新的远程地址                                         |
| `origin` | **远程仓库的别名**。 conventionally (惯例) 默认主远程仓库叫 `origin` |
| `URL`    | 远程仓库的 HTTPS 或 SSH 地址                                 |

若**已存在远程仓库**：

```bash
# 方式一：先删再加
# 1. 先删除现有的 origin
git remote remove origin

# 2. 再重新添加 Gitee 的地址
git remote add origin https://gitee.com/liyigiteehao/newtest.git

# 方式二：直接更新
# 直接将 origin 的地址设置为 Gitee 的仓库地址
git remote set-url origin https://gitee.com/liyigiteehao/newtest.git
```

连接成功后**查看远程 URL**：

```bash
git remote -v
```

### 7.2 推送与拉取：双向同步

实现本地与远程代码的同步。

#### 🚀 推送 (Push) - 上传代码

```bash
git push -u origin "master"
```

*   **拆解**：
    *   `push`：上传操作。
    *   `-u` (`--set-upstream`)：**关键参数**。设置上游分支，建立本地 `master` 与远程 `origin/master` 的追踪关系。
    *   `origin`：推送到哪个远程仓库（别名）。
    *   `master`：推送哪个分支（注：新版 Git 默认主分支可能为 `main`，请根据实际情况调整）。
*   **效果**：
    *   首次执行后，以后只需输入 `git push` 即可，无需再写长命令。
    *   远程仓库将出现你的代码。

#### 📥 拉取 (Pull) - 下载代码

```bash
git pull
```

*   **作用**：
    *   从远程仓库下载最新代码，并自动合并到本地当前分支。
    *   等价于 `git fetch` (下载) + `git merge` (合并)。
*   **场景**：
    *   多人协作时，开始前先 `pull` 防止冲突。
    *   换电脑工作时，拉取最新进度。

## 8 历史版本

### 7.1 查看历史版本

#### （1）基本语法

**git reflog**  **查看版本信息**

git reflog -n 数量

**git log**  **查看版本详细信息**

#### （2）案例实操

![image-20230627134228811](image\image-20230627134228811.png)



### 7.2 版本穿梭

#### （1）基本语法

**git reset --hard** **版本号**

#### （2）案例实操

--首先查看当前的历史记录，可以看到当前是在48f4e22这个版本

![image-20230627134422376](image\image-20230627134422376.png)

 

--切换到之前版本，8ca80d7版本，也就是我们第一次提交的版本

![image-20230627134533136](image\image-20230627134533136.png)

 

--切换完毕之后再查看历史记录，当前成功切换到了8ca80d7版本

![image-20230627134618381](image\image-20230627134618381.png)

 

--然后查看文件hello.txt，发现文件内容已经变化



 Git切换版本，底层其实是移动的HEAD指针。

# 第4章 Git客户端便捷操作

## 1. 安装部署

使用命令行操作git相对而言是非常不方便的，查看内容也不是很直观，所有官方推荐使用Git的GUI 客户端来完成页面化操作。

https://git-scm.com/downloads/guis

## 2. 连接GitHub远程仓库

![image-20250831153802651](image-20250831153802651.png)

## 3. Gitee替代GitHub

![image-20250831154130279](image-20250831154130279.png)

## 4. 开发工具兼容使用Git

（1）首先在pycharm中安装git，gitee，github等插件，并配置 

![image-20250831165128800](image-20250831165128800.png)

（2）先在pycharm中的项目初始化git

（3） 配置Git忽略文件，根目录下创建.gitignore文件

```text
### Python template
# Byte-compiled / optimized / DLL files
__pycache__/
*.py[cod]
*$py.class

# C extensions
*.so

# Distribution / packaging
.Python
build/
develop-eggs/
dist/
downloads/
eggs/
.eggs/
lib/
lib64/
parts/
sdist/
var/
wheels/
*.egg-info/
.installed.cfg
*.egg
MANIFEST

# PyInstaller
#  Usually these files are written by a python script from a template
#  before PyInstaller builds the exe, so as to inject date/other infos into it.
*.manifest
*.spec

# Installer logs
pip-log.txt
pip-delete-this-directory.txt

# Unit test / coverage reports
htmlcov/
.tox/
.coverage
.coverage.*
.cache
nosetests.xml
coverage.xml
*.cover
.hypothesis/

# Translations
*.mo
*.pot

# Sphinx documentation
docs/_build/

# PyBuilder
target/

# pyenv
.python-version

# celery beat schedule file
celerybeat-schedule

# Environments
.venv
venv/
ENV/
.envs/*
env.bak/
venv.bak/

# Rope project settings
.ropeproject

# mkdocs documentation
/site

# godie
.godie_cache/

# Logs
/logs/
*.log

# Runtime data
pids
*.pid
*.seed
*.pid.lock

# Directory for instrumented libs generated by jscoverage/JSCover
lib-cov

# Coverage directory used by tools like istanbul
coverage

# nyc test coverage
.nyc_output

# Bower dependency directory (https://bower.io/)
bower_components

# node-waf configuration
.lock-wscript

# Compiled binary addons (http://nodejs.org/api/addons.html)
build/Release

# Dependency directories
node_modules/
jspm_packages/

# Typescript v1 declaration files
typings/

# Optional npm cache directory
.npm

# Optional eslint cache
.eslintcache

# Optional REPL history
.node_repl_history

# Output of "npm pack"
*.tgz

# Yarn Integrity file
.yarn-integrity


### Linux template
*~

# temporary files which can be created if a process still has a handle open of a deleted file
.fuse_hidden*

# KDE directory preferences
.directory

# Linux trash folder which might appear on any partition or disk
.Trash-*

# .nfs files are created when an open file is removed but is still being accessed
.nfs*


### Project template
.pytest_cache/
.ipython/

# Django stuff:
godie/static/
godie/staticfiles/
godie/media/
.static_storage/

# Flask stuff:
instance/
.webassets-cache

# Scrapy stuff:
.scrapy

# Jupyter Notebook
.ipynb_checkpoints

# SageMath parsed files
*.sage.py

# Spyder project settings
.spyderproject
.spyproject

# pycharm
/.idea/
```

（4）初始化本地库

![image-20250831165921467](image-20250831165921467.png)

（8）提交到本地库

右键点击项目选择Git -> Add将项目添加到暂存区。

![image-20250831165953498](image-20250831165953498.png)

 

（9）切换版本

查看历史版本 

右键选择要切换的版本，然后在菜单里点击get。

# 第5章 GitLab的部署与使用    

## 为什么使用GitLab-开发运维一体化

企业一般都会部署自己的Git服务器，GitLab就是一个私有化部署的工具

使用git，还需要一个远程代码仓库。常见的github、gitee这种远程代码仓库，公司中一般不会使用，因为他们是使用外网的，不够安全。一般企业都会搭建一个仅内网使用的远程代码仓库，最常见就是 GitLab。

### 安装部署

GitLab一般由公司的运维人员安装部署，开发人员只需要申请账号和相应权限即可

 

# 第6章 企业项目构建与开发分支

## 1. GitFlow工作流介绍

在项目开发过程中使用 Git 的方式常见的有：

### **1.1 集中式工作流**

所有修改都提交到 Master 这个分支。比较适合极小团队或单人维护的项目，不建议使用这种方式。

![wps1](wps1.jpg)

### **1.2 功能开发工作流**

功能开发应该在一个专门的分支，而不是在 master 分支上。适用于小团队开发。

![img](image\wps21111.jpg) 

### **1.3 GitFlow工作流**

公司中最常用于管理大型项目。为功能开发、发布准备和维护设立了独立的分支，让发布迭代过程更流畅。

![image-20250902143544084](image-20250902143544084.png)

## 2. 各分支功能介绍

![image-20250902143550424](image-20250902143550424.png)

### 2.1 主干分支 master

主要负责管理正在运行的生产环境代码，永远保持与正在运行的生产环境完全一致。为了保持稳定性一般不会直接在这个分支上修改代码，都是通过其他分支合并过来的。

### 2.2 开发分支 develop

主要负责管理正在开发过程中的代码。一般情况下应该是最新的代码。

### 2.3 功能分支 feature

为了不影响较短周期的开发工作，一般把中长期开发模块，会从开发分支中独立出来。 开发完成后会合并到开发分支。

### 2.4 准生产分支（预发布分支） release

较大的版本上线前，会从开发分支中分出准生产分支，进行最后阶段的集成测试。该版本上线后，会合并到主干分支。生产环境运行一段时间较稳定后可以视情况删除。

### 2.5 bug 修理分支 hotfix

主要负责管理生产环境下出现的紧急修复的代码。 从主干分支分出，修复完毕并测试上线后，并回主干分支和开发分支。并回后，视情况可以删除该分支。

## 3. 创建项目与分支管理

首先在Gitee上面按照项目规格创建远程仓库。

![image-20250831174602335](image-20250831174602335.png)

### 3.1 从仓库创建项目

![image-20250831174656610](image-20250831174656610.png)

### 3.2 不同分支的提交与合并

（1）新建分支和切换分支

![image-20250831180525203](image-20250831180525203.png)

（2）不同分支提交代码与合并

首先在feature分支编写第一个模块的模拟代码，并提交

（3）合并feature到develop分支

利用Pull Requests发起合并请求，审核通过后可以合并到开发分支

![image-20250831181801202](image-20250831181801202.png)



# 第7章 冲突提交

实际单个模块的开发往往不是单独一个人来进行操作，当多个人协同开发相同的一个项目时，就会涉及到提交冲突的问题。

## 1. 不同人修改不同文件

（1）提交代码到远程仓库，此时会有报错信息

​	Git会智能识别，采用merge合并命令，拉取远端文件到本地进行合并。

（2）查看Git提交的全部历史记录，可以看到中间有拉取Gitee日志的部分

## 2. 不同人修改同文件的不同区域

同样可以采用merge命令，git会自动合并不同的区域代码。

## 3. 不同人修改同文件的相同区域

无法直接采用merge命令，需要人为判断哪些作为最终的结果来保留
