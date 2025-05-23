# 使用 Hugging Face Transformers 进行推理

使用 Hugging Face Transformers 库来运行 InternLM 模型。

## 安装

```bash
pip install transformers torch
```

## 基本推理

```python
import torch
from transformers import AutoTokenizer, AutoModelForCausalLM

# 加载模型和分词器
model_name = "InternLM/internlm3-8b-instruct"
tokenizer = AutoTokenizer.from_pretrained(model_name, trust_remote_code=True)
model = AutoModelForCausalLM.from_pretrained(
    model_name,
    trust_remote_code=True,
    torch_dtype=torch.float16,
    device_map="auto"
)

# 准备输入
prompt = "你好，请介绍一下你自己"
inputs = tokenizer(prompt, return_tensors="pt")

# 生成回复
with torch.no_grad():
    outputs = model.generate(
        inputs.input_ids,
        max_new_tokens=256,
        temperature=0.7,
        do_sample=True,
        pad_token_id=tokenizer.eos_token_id
    )

# 解码输出
response = tokenizer.decode(outputs[0], skip_special_tokens=True)
print(response)
```

## 流式生成

```python
from transformers import TextIteratorStreamer
import threading

streamer = TextIteratorStreamer(tokenizer, skip_prompt=True, skip_special_tokens=True)

generation_kwargs = dict(
    inputs.input_ids,
    streamer=streamer,
    max_new_tokens=256,
    temperature=0.7,
    do_sample=True,
    pad_token_id=tokenizer.eos_token_id
)

thread = threading.Thread(target=model.generate, kwargs=generation_kwargs)
thread.start()

for new_text in streamer:
    print(new_text, end="", flush=True)
```

## 批量推理

```python
prompts = [
    "什么是人工智能？",
    "请解释机器学习的概念",
    "深度学习有什么应用？"
]

inputs = tokenizer(prompts, return_tensors="pt", padding=True, truncation=True)

with torch.no_grad():
    outputs = model.generate(
        inputs.input_ids,
        attention_mask=inputs.attention_mask,
        max_new_tokens=128,
        temperature=0.7,
        do_sample=True,
        pad_token_id=tokenizer.eos_token_id
    )

responses = tokenizer.batch_decode(outputs, skip_special_tokens=True)
for prompt, response in zip(prompts, responses):
    print(f"问题: {prompt}")
    print(f"回答: {response}")
    print("-" * 50)
```

## 量化推理

```python
from transformers import BitsAndBytesConfig

# 4-bit 量化配置
quantization_config = BitsAndBytesConfig(
    load_in_4bit=True,
    bnb_4bit_compute_dtype=torch.float16,
    bnb_4bit_use_double_quant=True,
    bnb_4bit_quant_type="nf4"
)

# 加载量化模型
model = AutoModelForCausalLM.from_pretrained(
    model_name,
    trust_remote_code=True,
    quantization_config=quantization_config,
    device_map="auto"
)
```
