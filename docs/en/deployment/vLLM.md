# vLLM inference

refer to [installation](https://docs.vllm.ai/en/latest/getting_started/installation/index.html) to install the latest code of vllm

```bash
pip install vllm --pre --extra-index-url https://wheels.vllm.ai/nightly
```

inference code:

```python
from vllm import LLM, SamplingParams
llm = LLM(model="internlm/internlm3-8b-instruct")
sampling_params = SamplingParams(temperature=1, repetition_penalty=1.005, top_k=40, top_p=0.8)
system_prompt = """You are an AI assistant whose name is InternLM (书生·浦语).
- InternLM (书生·浦语) is a conversational language model that is developed by Shanghai AI Laboratory (上海人工智能实验室). It is designed to be helpful, honest, and harmless.
- InternLM (书生·浦语) can understand and communicate fluently in the language chosen by the user such as English and 中文."""
prompts = [
    {
        "role": "system",
        "content": system_prompt,
    },
    {
        "role": "user",
        "content": "Please tell me five scenic spots in Shanghai"
    },
]
outputs = llm.chat(prompts,
                   sampling_params=sampling_params,
                   use_tqdm=False)
print(outputs)
```
