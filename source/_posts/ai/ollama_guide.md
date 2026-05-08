# Ollama 本地部署大模型与调用指南

> 在自己电脑上跑一个大模型，零成本、零门槛

***

## 一、Ollama 是什么

**通俗理解**：Ollama 是大模型的"一键安装包"。以前想在自己电脑上跑一个大模型，要装 Python、PyTorch、CUDA，配置各种环境依赖，折腾一整天还不一定能跑起来。Ollama 把模型打包成一个可执行文件，下载安装后一条命令就能跑。

**类比**：

- 没有 Ollama：买一台游戏机→装系统→装驱动→装游戏→配置画质→终于能玩了
- 有 Ollama：把游戏卡插进卡槽→开机→直接玩

**核心特点**：

- 开源免费，支持 Windows / Mac / Linux
- 内置模型仓库，一条命令下载并启动模型
- 自带 OpenAI 兼容的 API 接口，可直接对接现有应用

***

## 二、安装 Ollama

### 2.1 下载

访问官网：[https://ollama.com](https://ollama.com)

根据你的操作系统下载安装包：

| 系统          | 安装方式                                                  |
| ----------- | ----------------------------------------------------- |
| **Mac**     | 下载 `.dmg` 文件，拖入 Applications                          |
| **Windows** | 下载 `.exe` 安装程序，双击安装                                   |
| **Linux**   | 终端执行 `curl -fsSL https://ollama.com/install.sh \| sh` |

### 2.2 验证安装

安装完成后打开终端（Windows 用 PowerShell 或 CMD）：

```bash
ollama --version
```

能输出版本号就说明安装成功了。

***

## 三、下载并运行模型

### 3.1 选择模型

Ollama 内置模型仓库，所有模型都在 [ollama.com/library](https://ollama.com/library) 可以找到。常用模型速览：

| 模型              | 大小                    | 特点           | 推荐用途       |
| --------------- | --------------------- | ------------ | ---------- |
| **llama3.2**    | 1B / 3B               | Meta 出品，轻量快速 | 日常对话、简单问答  |
| **qwen2.5**     | 0.5B / 7B / 14B / 32B | 阿里出品，中文能力强   | 中文写作、代码生成  |
| **deepseek-r1** | 1.5B / 7B / 14B / 32B | 推理能力突出       | 逻辑推理、数学计算  |
| **mistral**     | 7B                    | 欧洲开源，英文强     | 英文写作、翻译    |
| **phi4**        | 3B                    | 微软出品，小但精     | 轻量级任务、边缘设备 |

> **选型建议**：中文场景优先选 `qwen2.5`，英文场景选 `llama3.2`，推理任务选 `deepseek-r1`。模型越大效果越好，但对电脑内存和显存要求也越高。

### 3.2 下载模型

```bash
# 下载 Qwen2.5 7B（中文推荐）
ollama pull qwen2.5:7b

# 下载 Llama 3.2 3B（轻量级推荐）
ollama pull llama3.2:3b
```

下载速度取决于网络，模型文件通常几个 GB。

### 3.3 运行模型

```bash
# 启动对话
ollama run qwen2.5:7b
```

启动后直接进入对话模式：

```
>>> 你好，请用三句话介绍一下 AI
>>> 什么是机器学习？
>>> 帮我写一首关于春天的短诗
```

输入 `/bye` 或 `Ctrl+D` 退出对话。

### 3.4 查看所有已下载的模型

```bash
ollama list
```

输出示例：

```
NAME              ID           SIZE    MODIFIED
qwen2.5:7b        a1b2c3d4e5   4.7 GB  2 hours ago
llama3.2:3b       f6g7h8i9j0   2.0 GB  1 day ago
```

### 3.5 删除模型

```bash
ollama rm qwen2.5:7b
```

***

## 四、API 调用

Ollama 启动后会自动在本地运行一个 API 服务，地址是 `http://localhost:11434`。这意味着你可以通过 HTTP 请求调用模型，就像使用 OpenAI API 一样。

### 4.1 确认服务运行

```bash
curl http://localhost:11434
```

返回 `"Ollama is running"` 说明服务正常。

### 4.2 通过 HTTP 接口调用

```bash
curl http://localhost:11434/api/generate -d '{
  "model": "qwen2.5:7b",
  "prompt": "什么是 Transformer？用一句话解释。",
  "stream": false
}'
```

返回示例：

```json
{
  "model": "qwen2.5:7b",
  "response": "Transformer 是一种基于自注意力机制的深度学习架构，它能同时处理整个序列而不是逐字，让模型更快、更准地理解语言。",
  "done": true
}
```

### 4.3 通过 Python 调用

#### 方式一：直接用 requests 调 HTTP 接口

```python
import requests

url = "http://localhost:11434/api/generate"
payload = {
    "model": "qwen2.5:7b",
    "prompt": "用 Python 写一个计算 Fibonacci 数列的函数",
    "stream": False
}

response = requests.post(url, json=payload)
print(response.json()["response"])
```

#### 方式二：使用 ollama Python 包（推荐）

```bash
pip install ollama
```

```python
import ollama

# 简单对话
response = ollama.chat(
    model="qwen2.5:7b",
    messages=[
        {"role": "system", "content": "你是一个专业的程序员"},
        {"role": "user", "content": "用 Python 实现一个快速排序算法"}
    ]
)

print(response["message"]["content"])
```

#### 方式三：搭配 FastAPI 做 API 接口

```python
from fastapi import FastAPI
import ollama

app = FastAPI()

@app.post("/chat")
def chat(prompt: str):
    response = ollama.chat(
        model="qwen2.5:7b",
        messages=[{"role": "user", "content": prompt}]
    )
    return {"answer": response["message"]["content"]}
```

启动后 `POST http://localhost:8000/chat` 就能调用本地模型。

***

## 五、实战：Ollama + Dify 搭配使用

> Dify 是课程中的低代码 AI 平台，搭配 Ollama 可以零成本搭建自己的 AI 应用。

1. 确保 Ollama 已启动：`ollama run qwen2.5:7b`
2. 确保 Ollama 允许外部访问（见下方注意事项）
3. 在 Dify 中添加模型提供者 → 选择 "Ollama" → 填入 API 地址 `http://localhost:11434`
4. 即可在 Dify 低代码平台中使用本地模型

***

## 六、常见问题

### Q1：Ollama 运行后电脑很卡怎么办？

大模型吃内存。7B 模型大约需要 8GB 内存，14B 需要 16GB。如果电脑配置不够：

- 换更小的模型，如 `qwen2.5:0.5b` 或 `llama3.2:1b`
- 关闭其他占用内存的程序

### Q2：中文回答效果不好怎么办？

- 确保用的是中文能力强的模型（`qwen2.5`、`deepseek-r1`）
- 英文模型如 `llama3.2` 中文能力较弱
- 在 system prompt 中明确指定用中文回答

### Q3：Dify 或其他应用连接不上 Ollama？

Ollama 默认只允许本机（localhost）访问。如果需要被 Docker 容器或其他机器访问，需要设置环境变量：

**Windows**：

```powershell
# 设置环境变量后重启 Ollama
set OLLAMA_HOST=0.0.0.0
```

**Mac / Linux**：

```bash
export OLLAMA_HOST=0.0.0.0
ollama serve
```

或在 Windows 系统环境变量中永久设置 `OLLAMA_HOST=0.0.0.0`。

### Q4：能用 GPU 加速吗？

Ollama 会自动检测 GPU：

- Mac M 系列芯片自动使用 Metal 加速
- Windows / Linux 有 NVIDIA 显卡的自动使用 CUDA 加速
- 没有 GPU 则用 CPU 运行，速度会慢一些但不影响功能

***

## 七、总结

| 步骤        | 命令                                    | 说明        |
| --------- | ------------------------------------- | --------- |
| 1. 安装     | 官网下载安装包                               | 一行命令或双击即可 |
| 2. 下载模型   | `ollama pull qwen2.5:7b`              | 选一个适合的模型  |
| 3. 对话     | `ollama run qwen2.5:7b`               | 终端直接对话    |
| 4. API 调用 | `http://localhost:11434/api/generate` | 代码中调用     |
| 5. 搭配平台   | Dify / LangChain 等                    | 低代码或框架集成  |

一句话总结：**Ollama 让大模型从云端回到本地，一条命令就能在自己的电脑上跑 AI。**

***
