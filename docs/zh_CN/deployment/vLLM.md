# 使用 vLLM 部署 InternLM

vLLM 是一个高吞吐量、内存高效的 LLM 推理和服务引擎。

## 安装

```bash
pip install vllm
```

## 离线推理

```python
from vllm import LLM, SamplingParams

# 创建 LLM 实例
llm = LLM(model="InternLM/internlm3-8b-instruct")

# 设置采样参数
sampling_params = SamplingParams(temperature=0.7, top_p=0.9, max_tokens=256)

# 准备提示
prompts = [
    "你好，请介绍一下你自己",
    "什么是人工智能？"
]

# 生成文本
outputs = llm.generate(prompts, sampling_params)

# 打印结果
for output in outputs:
    prompt = output.prompt
    generated_text = output.outputs[0].text
    print(f"提示: {prompt!r}")
    print(f"生成文本: {generated_text!r}")
```

## OpenAI 兼容服务器

启动与 OpenAI API 兼容的服务器：

```bash
python -m vllm.entrypoints.openai.api_server \
    --model InternLM/internlm3-8b-instruct \
    --host 0.0.0.0 \
    --port 8000
```

## 客户端调用

```python
from openai import OpenAI

# 创建客户端
client = OpenAI(
    base_url="http://localhost:8000/v1",
    api_key="your-api-key-here",  # vLLM 不验证 API key
)

# 聊天补全
completion = client.chat.completions.create(
    model="InternLM/internlm3-8b-instruct",
    messages=[
        {"role": "user", "content": "你好，请介绍一下深度学习"}
    ]
)

print(completion.choices[0].message.content)
```
