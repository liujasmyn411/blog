# WSL 与 Docker 入门指南

> 在 Windows 上使用 Linux 和容器化开发环境

***

## 一、WSL（Windows Subsystem for Linux）

### 是什么

WSL 是 Windows 系统内置的 Linux 兼容层，让你不用装虚拟机、不用双系统，就能在 Windows 上直接运行 Linux 命令行工具和完整 Linux 发行版（如 Ubuntu、Debian 等）。

- **WSL 1**：兼容性翻译层，文件系统性能好，但不支持 Docker 等需要完整 Linux 内核的场景
- **WSL 2**：真正的 Linux 内核运行在轻量虚拟机中，支持完整的系统调用和 Docker

**推荐直接使用 WSL 2。**

### 官网

- 官方文档：[https://learn.microsoft.com/zh-cn/windows/wsl/](https://learn.microsoft.com/zh-cn/windows/wsl/)
- GitHub 仓库：[https://github.com/microsoft/WSL](https://github.com/microsoft/WSL)

### 安装步骤

> 系统要求：Windows 10 版本 2004 及以上，或 Windows 11

**一键安装（推荐）**

以管理员身份打开 PowerShell 或 CMD，执行：

```powershell
wsl --install
```

这条命令会自动完成：
1. 启用 WSL 和虚拟机平台组件
2. 下载并安装 Ubuntu（默认发行版）
3. 设置 WSL 2 为默认版本

安装完成后**重启电脑**，首次启动 Ubuntu 时会提示你设置用户名和密码。

**指定发行版安装**

```powershell
# 查看可用发行版
wsl --list --online

# 安装指定发行版（如 Debian）
wsl --install -d Debian
```

**验证安装**

```powershell
# 查看已安装的发行版和版本
wsl --list --verbose
# 或简写
wsl -l -v
```

输出应显示 `VERSION` 为 `2`。

**常用命令速查**

| 命令 | 说明 |
|------|------|
| `wsl` | 启动默认发行版 |
| `wsl -d <发行版名>` | 启动指定发行版 |
| `wsl --shutdown` | 关闭所有 WSL 实例 |
| `wsl --update` | 更新 WSL 内核 |
| `wsl --set-version <发行版名> 2` | 转换为 WSL 2 |
| `wsl --set-default-version 2` | 设置默认版本为 WSL 2 |

**从 Windows 访问 Linux 文件**

在 WSL 终端中，Windows 的 C 盘挂载在 `/mnt/c`：

```bash
cd /mnt/c/Users/你的用户名
```

**从 Linux 访问 Windows 文件**

在 Windows 文件资源管理器地址栏输入 `\\wsl$` 即可访问。

***

## 二、Docker

### 是什么

Docker 是一个容器化平台，把应用及其所有依赖（代码、运行时、库、配置）打包成一个"容器"，在任何安装了 Docker 的环境中运行，结果完全一致——"在我机器上能跑"不再是问题。

- **镜像（Image）**：打包好的应用模板，只读
- **容器（Container）**：镜像的运行实例，可随时创建、启动、停止、删除
- **Dockerfile**：定义如何构建镜像的脚本文件

### 官网

- 官方文档：[https://docs.docker.com/](https://docs.docker.com/)
- 下载页面：[https://www.docker.com/products/docker-desktop/](https://www.docker.com/products/docker-desktop/)
- Docker Hub：[https://hub.docker.com/](https://hub.docker.com/)

### 安装步骤（Windows + WSL 2 后端）

> 系统要求：Windows 10 2004+ 或 Windows 11，WSL 2 已安装

**1. 下载 Docker Desktop**

访问 [Docker Desktop 下载页面](https://www.docker.com/products/docker-desktop/)，选择 Windows 版本下载安装包，双击安装。

安装完成之后，Docker拉取资源会很慢，需要换源：

**Docker千问换源：**
<img src="./images/Docker千问换源示意图.png" >

**Docker搜索引擎换源:**
<img src="./images/Docker搜索引擎换源示意图.png" >

**Docker自带AI换源:**
<img src="./images/Docker自带AI换源示意图.png" >

**2. 配置 WSL 2 后端**

安装完成后启动 Docker Desktop：
- 进入 Settings → General → 勾选 "Use WSL 2 based engine"（默认已勾选）
- 进入 Settings → Resources → WSL Integration → 勾选你使用的 Linux 发行版（如 Ubuntu）

**3. 验证安装**

打开 PowerShell 或 WSL 终端：

```bash
docker --version
docker compose version
docker run hello-world
```

最后一条命令如果输出 "Hello from Docker!" 说明一切正常。

**注意**：Docker Desktop 对商业用户（公司规模超过 250 人或年收入超过 1000 万美元）需要付费许可证，个人使用和小型团队免费。

**免费替代方案**：
- [Docker Engine（直接在 WSL 2 内安装）](https://docs.docker.com/engine/install/)——完全免费
- [Podman](https://podman.io/)——开源无许可证限制


### Docker desktop 详解


### 快速上手 [后面部署会细讲]

```bash
# 拉取一个 Nginx 镜像
docker pull nginx

# 运行容器，端口映射 8080->80
docker run -d -p 8080:80 nginx

# 查看运行中的容器
docker ps

# 停止容器
docker stop <容器ID>

# 删除容器
docker rm <容器ID>
```

### Dockerfile 示例 [后面部署会细讲]

创建一个名为 `Dockerfile` 的文件：

```dockerfile
# 基于 Python 3.12 镜像
FROM python:3.12-slim

# 设置工作目录
WORKDIR /app

# 复制代码
COPY . .

# 安装依赖
RUN pip install --no-cache-dir -r requirements.txt

# 启动应用
CMD ["python", "app.py"]
```

构建并运行：

```bash
# 构建镜像
docker build -t my-app .

# 运行
docker run -p 5000:5000 my-app
```

***

## 三、WSL + Docker 常用工作流

| 场景 | 操作 |
|------|------|
| 在 WSL 中开发，Docker 运行 | VSCode 连接 WSL 写代码，在 WSL 终端执行 `docker run` |
| 数据持久化 | 用 `docker volume` 或将 Windows 目录挂载到容器中 |
| 数据库开发 | `docker run -d -p 3306:3306 -e MYSQL_ROOT_PASSWORD=123 mysql` |
| 前端开发 | `docker run -p 3000:3000 node:18-alpine` 跑 Node 服务 |

***

## 总结

| | WSL | Docker |
|---|-----|--------|
| **作用** | 在 Windows 上跑 Linux | 把应用打包成可移植的容器 |
| **关系** | Docker Desktop 依赖 WSL 2 作为后端引擎 | 在 WSL 2 上运行最流畅 |
| **开发者价值** | 不用装虚拟机就有完整的 Linux 环境 | 开发和生产环境一致，部署不踩坑 |

推荐安装顺序：**先装 WSL 2 → 再装 Docker Desktop → 开启容器化开发**。

***
