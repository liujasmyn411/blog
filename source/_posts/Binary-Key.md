---
title: Binary-Key 
date: 2025-12-15
tags: 
---
[官方文档](https://metis.builders/docs/binary-key)显示 Metis Self-hosted API Binary 需要使用 Binary Key 以获取报价和构建交换交易服务。**所有请求都需要一个有效的 Binary Key。**

下面是获取 Binary Key 的步骤：
#### 质押 Jup
1. 连接你的 Solana 钱
2. 输入质押数量
3. 确认并签署交易
4. 等待确认
具体步骤见另一篇文章[Stake-Jup](https://liujasmyn411.github.io/blog/2025/12/15/Stake-Jup/)

#### 填写申请
1. 连接钱包
质押足够的 Jup 后，进入[Portal](https://portal.metis.builders/)填写申请，注意需使用**质押 Jup 的钱包**连接。
2. 填写信息
连接成功后填入必要的信息如：Email、Telegram、GitHub URL 和申请原因。填写完成后，点击 request access 申请访问等待审核，如有后续问题可以进入 Jupiter 官方 Discord 进行提问。Binary Key 申请成功后通过你**填写的电子邮件**接收。

<img src="/blog/images/Portal.png" title="Portal" width="400px"/>

**注意：绝对不要将 Binary Key 提交到版本控制系统，或是在客户端代码中暴露它。请使用环境变量来安全地存储 Binary Key。**

#### 解除质押
如果你想取回代币在[https://vote.jup.ag/](https://vote.jup.ag/)界面点击 Unstake 发起解除质押。

参考
[https://metis.builders/docs/binary-key#request-binary-key](https://metis.builders/docs/binary-key#request-binary-key)
