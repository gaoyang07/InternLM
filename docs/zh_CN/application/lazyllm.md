# 使用 LazyLLM 部署 InternLM

LazyLLM 是一个低代码构建大模型应用的开发工具，为大模型应用开发和部署提供了便捷的解决方案。

## 安装

```bash
pip install lazyllm
```

## 基本用法

### 简单的模型调用

```python
import lazyllm

# 创建模型实例
llm = lazyllm.OnlineChatModule(
    model="InternLM/internlm3-8b-instruct",
    stream=False
)

# 进行对话
response = llm("你好，请介绍一下你自己")
print(response)
```

### 构建应用流程

```python
import lazyllm

# 定义提示模板
prompt_template = lazyllm.PromptTemplate(
    template="你是一个有帮助的助手。请回答以下问题：{question}"
)

# 创建模型
llm = lazyllm.OnlineChatModule(model="InternLM/internlm3-8b-instruct")

# 构建流程
flow = prompt_template | llm

# 执行
result = flow(question="什么是人工智能？")
print(result)
```

### 多模型协作

```python
import lazyllm

# 创建多个模型实例
llm1 = lazyllm.OnlineChatModule(model="InternLM/internlm3-8b-instruct")
llm2 = lazyllm.OnlineChatModule(model="InternLM/internlm3-8b-instruct")

# 定义不同的角色
expert1 = lazyllm.PromptTemplate("作为技术专家，请分析：{topic}") | llm1
expert2 = lazyllm.PromptTemplate("作为商业专家，请分析：{topic}") | llm2

# 并行执行
results = lazyllm.parallel(expert1, expert2)(topic="人工智能的发展前景")
print("技术专家观点：", results[0])
print("商业专家观点：", results[1])
```

## Web 应用部署

```python
import lazyllm

# 创建 Web 应用
app = lazyllm.WebApp()

# 添加聊天界面
chat_interface = lazyllm.ChatInterface(
    llm=lazyllm.OnlineChatModule(model="InternLM/internlm3-8b-instruct")
)

app.add_component(chat_interface)

# 启动服务
app.start(port=8080)
```

## RAG 应用

```python
import lazyllm

# 创建知识库
knowledge_base = lazyllm.VectorStore()
knowledge_base.add_documents([
    "这是一些示例文档内容...",
    "更多的知识库内容..."
])

# 创建 RAG 流程
rag_flow = lazyllm.RAGModule(
    retriever=knowledge_base,
    llm=lazyllm.OnlineChatModule(model="InternLM/internlm3-8b-instruct")
)

# 查询
answer = rag_flow("基于知识库，请回答这个问题")
print(answer)
```
