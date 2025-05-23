# 使用 SGLang 部署 InternLM

SGLang 是一个高效的结构化生成语言运行时，为大语言模型提供快速服务。

## 安装

```bash
pip install "sglang[all]"
```

## 启动服务器

```bash
python -m sglang.launch_server --model-path InternLM/internlm3-8b-instruct --host 127.0.0.1 --port 30000
```

## 使用客户端

```python
import sglang as sgl

@sgl.function
def multi_turn_question(s, question_1, question_2):
    s += sgl.system("你是一个有帮助的助手。")
    s += sgl.user(question_1)
    s += sgl.assistant(sgl.gen("answer_1", max_tokens=256))
    s += sgl.user(question_2)
    s += sgl.assistant(sgl.gen("answer_2", max_tokens=256))

# 设置后端
sgl.set_default_backend(sgl.Runtime(model_path="InternLM/internlm3-8b-instruct"))

# 运行对话
state = multi_turn_question.run(
    question_1="什么是机器学习？",
    question_2="它与深度学习有什么区别？"
)

print("问题1回答:", state["answer_1"])
print("问题2回答:", state["answer_2"])
```

## OpenAI 兼容 API

SGLang 也提供了与 OpenAI 兼容的 API 接口：

```python
import openai

client = openai.Client(
    base_url="http://127.0.0.1:30000/v1",
    api_key="EMPTY"
)

response = client.chat.completions.create(
    model="InternLM/internlm3-8b-instruct",
    messages=[
        {"role": "user", "content": "你好，请介绍一下你自己"}
    ],
    temperature=0.7,
    max_tokens=256
)

print(response.choices[0].message.content)
```

## 特性

- 结构化生成支持
- 高效的内存管理
- 并行推理
- OpenAI 兼容接口
