# [LazyLLM](https://github.com/LazyAGI/LazyLLM)

LazyLLM is an framework which supports the easiest and laziest way for building multi-agent LLMs applications. It offers extremely high flexibility and ease of use compared to LangChain and LLamaIndex.

When you have installed `lazyllm` by `pip3 install lazyllm` and `lazyllm install standard`, you can use the following code to build chatbots based on internLM at a very low cost, without worrying about the special tokens (such as `<|im_start|>system` and `<|im_end|>`) of the dialogue model. Don’t worry about not having weight files; as long as you are connected to the internet, the code below will automatically download the weight files and deploy the service for you. Enjoy the convenience that LazyLLM brings to you.

```python
from lazyllm import TrainableModule, WebModule
# Model will be download automatically if you have an internet connection
m = TrainableModule('internlm2_5-7b-chat')
# will launch a chatbot server
WebModule(m).start().wait()
```

You can use the following code to finetune your model if needed. When the trainset (The dataset needs to be downloaded to the local machine, for example:[
alpaca_gpt4_zh](https://huggingface.co/datasets/llamafactory/alpaca_gpt4_zh) of the TrainableModule is set, during the calling of the WebModule's update function, the TrainableModule will be automatically fine-tuned, and then both the TrainableModule and the WebModule will be deployed separately.

```python
from lazyllm import TrainableModule, WebModule
m = TrainableModule('internlm2-chat-7b').trainset('/path/to/your_data.json').mode('finetune')
WebModule(m).update().wait()
```

It is worth mentioning that regardless of which model in the InternLM series you use, you can perform inference and fine-tuning with LazyLLM. You don't need to worry about the model's segmentation strategy or special tokens.<br>
If you want to build your own RAG application, you don't need to first start the inference service and then configure the IP and port to launch the application like you would with LangChain. Refer to the code below, and with LazyLLM, you can use the internLM series models to build a highly customized RAG application in just ten lines of code, along with document management services (The document requires specifying the local absolute path. You can download it as an example from here: [rag_master](https://huggingface.co/datasets/Jing0o0Xin/rag_master)):

<details>
<summary>Click here to get imports and prompts</summary>

```python
import os
import lazyllm
from lazyllm import pipeline, parallel, bind, SentenceSplitter, Document, Retriever, Reranker

prompt = 'You will play the role of an AI Q&A assistant and complete a dialogue task. In this task, you need to provide your answer based on the given context and question.'
```

</details>

```python
documents = Document(dataset_path='/file/to/yourpath', embed=lazyllm.TrainableModule('bge-large-zh-v1.5'), create_ui=False)
documents.create_node_group(name="sentences", transform=SentenceSplitter, chunk_size=1024, chunk_overlap=100)
with pipeline() as ppl:
    with parallel().sum as ppl.prl:
        prl.retriever1 = Retriever(documents, group_name="sentences", similarity="cosine", topk=3)
        prl.retriever2 = Retriever(documents, "CoarseChunk", "bm25_chinese", 0.003, topk=3)
    ppl.reranker = Reranker("ModuleReranker", model="bge-reranker-large", topk=1) | bind(query=ppl.input)
    ppl.formatter = (lambda nodes, query: dict(context_str="".join([node.get_content() for node in nodes]), query=query)) | bind(query=ppl.input)
    ppl.llm = lazyllm.TrainableModule("internlm2_5-7b-chat").prompt(lazyllm.ChatPrompter(prompt, extro_keys=["context_str"]))
lazyllm.WebModule(ppl, port=23456).start().wait()
```

LazyLLM Documents: https://docs.lazyllm.ai/
