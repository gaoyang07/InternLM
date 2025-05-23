# 本地聊天

在本地环境中与 InternLM 进行对话。

## 基本用法

```python
import torch
from transformers import AutoTokenizer, AutoModelForCausalLM

tokenizer = AutoTokenizer.from_pretrained("InternLM/internlm3-8b-instruct", trust_remote_code=True)
model = AutoModelForCausalLM.from_pretrained("InternLM/internlm3-8b-instruct", trust_remote_code=True, torch_dtype=torch.float16, device_map="auto")
model = model.eval()

response, history = model.chat(tokenizer, "你好", history=[])
print(response)
```
