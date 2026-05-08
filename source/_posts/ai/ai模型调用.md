封装函数的好处主要体现在以下几点
1. 代码复用
```python
# 未封装：每次调用都要写一堆配置
client = OpenAI(api_key=os.getenv("DASHSCOPE_API_KEY"), base_url="...")
completion = client.chat.completions.create(model="qwen-plus", messages=[...])

# 封装后：一行搞定
response = chat("你好")
```
2. 统一管理
- API 地址、默认模型等配置集中在一处
- 后续需要修改（如换模型、换API）只需改一处

3. 降低使用门槛
- 其他项目引用时，无需关心底层实现
- 只需传入 prompt，不需要懂 OpenAI、messages 等概念

4. 便于扩展
后续可以快速添加功能，如：

- 添加日志记录
- 添加重试机制
- 添加流式输出
- 添加对话历史