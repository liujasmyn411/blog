---
title: 智谱以及如何在 Discord 对接 openclaw 的 bot 客服
date: 2026-02-11
tags: ai
---
### 1 智谱是什么
[智谱 AI 开放平台](https://bigmodel.cn/)是北京智谱华章科技有限公司推出的一站式人工智能大模型服务平台。

它主要面向开发者和企业，提供基于 GLM 系列大模型的 API 接口及相关开发工具。简单来说，我们可以通过这个平台把智谱的 AI 能力集成到你自己的开发项目中。

### 2 核心内容
#### 1.核心模型矩阵
平台托管了智谱自主研发的全模态模型，涵盖了不同的应用场景：

语言模型 (GLM-4 / GLM-3.5)：用于对话、创作、代码生成和逻辑推理。

多模态模型 (CogVLM / GLM-4V)：能够理解图片内容并进行问答。

图像生成 (CogView)：支持根据文字描述生成高质量图片。

视频生成 (CogVideo)：支持文生视频、图生视频以及首尾帧生成。

向量模型 (Embedding)：用于构建知识库检索（RAG）和语义搜索。

#### 2.主要功能与服务
API 调用：提供标准 RESTful API，兼容 OpenAI SDK 协议，方便开发者低成本迁移。

智能体中心 (Agent)：支持零代码或低代码构建 AI 智能体，集成外部工具（如搜索、计算器、代码解释器）。

模型精调 (Fine-tuning)：允许用户上传自有数据对模型进行微调，以适应特定的行业需求。

长文本支持：部分模型支持极长的上下文输入（如 GLM-4-Long），适合处理长篇文档或复杂代码库。

### 3 用 GLM-Flash 模型对接 openclaw 的 bot 客服
#### 1.准备 Discord Bot
1. 获取 Bot Token
访问 [Discord Developer Portal](https://discord.com/developers/applications)，点击 New Application，起个名字。从左侧进入 Bot 选项卡，点击 Reset Token 获取你的 **Bot Token**，需要输入你的 discord 密码才能获取。

**注意**：向下滚动找到 Privileged Gateway Intents，开启 Presence Intent、Server Members Intent、Message Content Intent。

2. 复制 Generated URL
从左侧进入 OAuth2 选项卡进入 OAuth2，勾选 bot 和 Administrator 或具体权限。复制生成的链接，并在浏览器打开，将机器人邀请进你的群组。

#### 2.获取 GLM-Flash 的 API Key
访问 [智谱 AI 开放平台](https://bigmodel.cn/)，点击右上角的控制台，进入后选择 GLM-4.7 API 接入。可能无法复制 API Key，创建一个新的就好啦。
<img src="/blog/images/GLM1.png" title="GLM1" width="400px"/>

#### 3.配置 OpenClaw
当你拿到了新的智谱 API Key 和 Discord Bot Token 后，回到你的 Ubuntu 终端
```bash
vim ~/.openclaw/openclaw.json
```
之后会让你输入 Bot Token 和 API Key 并进行其他基础配置。比如

Default model，我选择了 zai/glm-4.7-flash。

Discord channels access，选择 Allowlist，因为这是比较安全的操作方式。机器人只会响应你明确授权的频道。这能防止机器人在不相关的频道里产生不必要的回复。

Discord channels allowlist，这一步是让你指定机器人只在哪些频道里说话。

还会让你安装用于查询地理位置、周边商家信息的插件，这并不是 bot 的核心工作，可以不安装。

Enable hooks，可以选择 session-memory 和 command-logger。

最后让你给机器人设定“人设”，我是“智简客服”，一个基于 GLM-Flash 的智能助手。请称呼我为“小助”。我的回答风格：简单明了，不使用难懂的术语，优先提供解决问题的步骤。

#### 4.测试
可以直接在 discord 频道里，艾特机器人。看他回不回复。


