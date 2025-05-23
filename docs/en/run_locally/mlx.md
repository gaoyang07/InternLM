# [mlx](https://github.com/ml-explore/mlx)

MLX is an array framework for machine learning research on Apple silicon, brought to you by Apple machine learning research.

With the following steps, you can perform InternLM2 or InternLM2.5 inference on Apple devices.

- Installation

```shell
pip install mlx mlx-lm
```

- Inference

```python
from mlx_lm import load, generate
tokenizer_config = {"trust_remote_code": True}
model, tokenizer = load("internlm/internlm2-chat-1_8b", tokenizer_config=tokenizer_config)
response = generate(model, tokenizer, prompt="write a story", verbose=True)
```
