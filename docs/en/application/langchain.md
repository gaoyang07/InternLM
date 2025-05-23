# [LangChain](https://github.com/langchain-ai/langchain)

LangChain is a framework for developing applications powered by large language models (LLMs).

You can build a [LLM chain](https://python.langchain.com/v0.1/docs/get_started/quickstart/#llm-chain) by the OpenAI API. And the server is recommended to be launched by LMDeploy, vLLM or others that are compatible with openai server.

```python
from langchain_openai import ChatOpenAI
from langchain_core.prompts import ChatPromptTemplate

llm = ChatOpenAI(
    model_name="a-model",
    openai_api_key="a dummy key",
    openai_api_base='https://0.0.0.0:23333/v1')
prompt = ChatPromptTemplate.from_messages([
    ("system", "You are a world class technical documentation writer."),
    ("user", "{input}")
])

chain = prompt | llm

chain.invoke({"input": "how can langsmith help with testing?"})
```

Or you can follow the guide [here](https://python.langchain.com/v0.1/docs/get_started/quickstart/#llm-chain) and run an ollama model locally.

As for other user cases, please look for them from [here](https://python.langchain.com/v0.1/docs/get_started/introduction/).
