# [ollama](https://github.com/ollama/ollama)

Ollama bundles model weights, configuration, and data into a single package, defined by a Modelfile. It optimizes setup and configuration details, enabling users to easily set up and execute LLMs locally (in CPU and GPU modes).

## Installation

Install ollama and pull the model

```bash
# install ollama
curl -fsSL https://ollama.com/install.sh | sh
# pull the model
ollama pull internlm/internlm3-8b-instruct
# install ollama-python
pip install ollama
```

## Inference with Ollama

```python
import ollama

system_prompt = """You are an AI assistant whose name is InternLM (书生·浦语).
- InternLM (书生·浦语) is a conversational language model that is developed by Shanghai AI Laboratory (上海人工智能实验室). It is designed to be helpful, honest, and harmless.
- InternLM (书生·浦语) can understand and communicate fluently in the language chosen by the user such as English and 中文."""

messages = [
    {
        "role": "system",
        "content": system_prompt,
    },
    {
        "role": "user",
        "content": "Please tell me five scenic spots in Shanghai"
    },
]

stream = ollama.chat(
    model='internlm/internlm3-8b-instruct',
    messages=messages,
    stream=True,
)

for chunk in stream:
  print(chunk['message']['content'], end='', flush=True)
```
