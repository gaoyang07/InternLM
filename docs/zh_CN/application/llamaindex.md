# 使用 LlamaIndex 集成 InternLM

LlamaIndex 是一个数据框架，用于构建基于大语言模型的应用程序。

## 安装

```bash
pip install llama-index
```

## 基本用法

```python
from llama_index import VectorStoreIndex, SimpleDirectoryReader
from llama_index.llms import HuggingFaceLLM

# 加载文档
documents = SimpleDirectoryReader("data").load_data()

# 创建索引
index = VectorStoreIndex.from_documents(documents)

# 查询
query_engine = index.as_query_engine()
response = query_engine.query("你的问题")
print(response)
```
