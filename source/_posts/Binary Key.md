---
title: Binary Key
date: 2025-12-15
tags: 
---
[官方文档](https://metis.builders/docs/binary-key)显示 Metis Self-hosted API Binary 需要使用 Binary Key 以获取报价和构建交换交易服务。**所有请求都需要一个有效的二进制密钥。**

下面是获取 Binary Key 的步骤：
#### 质押 Jup
1. 连接你的 Solana 钱包
首先要在[https://vote.jup.ag/](https://vote.jup.ag/)质押 Jup，点击页面右上角的“Connect Wallet”​ 按钮，连接你的 **Solana 钱包**，保证钱包里有**至少 10000 Jup** 用于质押，并保留少量 Sol 作为交易手续费。
2. 输入质押数量：
在质押页面，输入你希望质押的 Jup 数量（至少 10000 Jup）。
3. 确认并签署交易：
点击“Stake Jup”​ 按钮，仔细检查交易详情，然后确认签名。
4. 等待确认：
交易提交到区块链后，等待几秒钟即可确认。成功后，你的质押状态会立即更新。
注意：质押后可以领取投票权参与 Jupiter DAO 的治理。 

#### 填写申请
1. 连接钱包
质押足够的 Jup 后，进入[Portal](https://portal.metis.builders/)填写申请，注意需使用**质押 Jup 的钱包**连接。
2. 填写信息
连接成功后填入必要的信息如：Email、Telegram、GitHub URL 和申请原因。填写完成后，点击 request access 申请访问等待审核，如有后续问题可以进入 Jupiter 官方 Discord 进行提问。Binary Key 申请成功后通过你**填写的电子邮件**接收。

**注意：绝对不要将二进制密钥提交到版本控制系统，或是在客户端代码中暴露它。请使用环境变量来安全地存储二进制密钥。**

#### 解除质押
如果你想取回代币在[https://vote.jup.ag/](https://vote.jup.ag/)界面点击 Unstake 发起解除质押。


