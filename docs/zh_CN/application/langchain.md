# 使用 LangChain 集成 InternLM

LangChain 是一个用于开发由大语言模型驱动的应用程序的框架。

## 安装

```bash
pip install langchain langchain-community
```

## 基本用法

### 初始化 InternLM

```python
from langchain.llms import HuggingFacePipeline
import transformers

# 加载模型和分词器
model_name = "InternLM/internlm3-8b-instruct"
tokenizer = transformers.AutoTokenizer.from_pretrained(model_name)
model = transformers.AutoModelForCausalLM.from_pretrained(model_name)

# 创建文本生成管道
pipe = transformers.pipeline(
    "text-generation",
    model=model,
    tokenizer=tokenizer,
    max_new_tokens=256,
    temperature=0.7
)

# 创建 LangChain LLM
llm = HuggingFacePipeline(pipeline=pipe)
```

### 简单的文本生成

```python
from langchain.prompts import PromptTemplate

template = """问题: {question}

回答: """

prompt = PromptTemplate(template=template, input_variables=["question"])

llm_chain = prompt | llm

response = llm_chain.invoke({"question": "什么是机器学习？"})
print(response)
```

### 构建聊天机器人

```python
from langchain.schema import HumanMessage, AIMessage
from langchain.memory import ConversationBufferMemory
from langchain.chains import ConversationChain

# 创建对话内存
memory = ConversationBufferMemory()

# 创建对话链
conversation = ConversationChain(
    llm=llm,
    memory=memory,
    verbose=True
)

# 进行对话
response1 = conversation.predict(input="你好，我是李明")
print("回应1:", response1)

response2 = conversation.predict(input="你还记得我的名字吗？")
print("回应2:", response2)
```

## 高级应用

### RAG (检索增强生成)

```python
from langchain.vectorstores import Chroma
from langchain.embeddings import HuggingFaceEmbeddings
from langchain.text_splitter import CharacterTextSplitter
from langchain.chains import RetrievalQA

# 准备文档
documents = ["这里是一些示例文档内容..."]

# 文本分割
text_splitter = CharacterTextSplitter(chunk_size=1000, chunk_overlap=0)
texts = text_splitter.create_documents(documents)

# 创建向量存储
embeddings = HuggingFaceEmbeddings()
docsearch = Chroma.from_documents(texts, embeddings)

# 创建 RAG 链
qa = RetrievalQA.from_chain_type(
    llm=llm,
    chain_type="stuff",
    retriever=docsearch.as_retriever()
)

# 提问
query = "告诉我关于文档的内容"
response = qa.run(query)
print(response)
```
