# LMDeploy

[LMDeploy](https://github.com/InternLM/lmdeploy) is an efficient, user-friendly toolkit designed for compressing, deploying, and serving LLM models.

This article primarily highlights the basic usage of LMDeploy. For a comprehensive understanding of the toolkit, we invite you to refer to [the tutorials](https://lmdeploy.readthedocs.io/en/latest/).

## Installation

Install lmdeploy with pip (python 3.8+)

```shell
pip install lmdeploy>=0.2.1
```

## Inference with LMDeploy

### Offline batch inference

You can run batch inference locally with the following python code:

```python
import lmdeploy
model_dir = "internlm/internlm3-8b-instruct"
pipe = lmdeploy.pipeline(model_dir)
response = pipe("Please tell me five scenic spots in Shanghai")
print(response)
```

With dynamic ntk, LMDeploy can handle a context length of 200K for `InternLM3`:

```python
from lmdeploy import pipeline, TurbomindEngineConfig
engine_config = TurbomindEngineConfig(session_len=200000,
                                      rope_scaling_factor=2.0)
pipe = pipeline("internlm/internlm3-8b-instruct", backend_engine=engine_config)
gen_config = GenerationConfig(top_p=0.8,
                              top_k=40,
                              temperature=0.8,
                              max_new_tokens=1024)
response = pipe(prompt, gen_config=gen_config)
print(response)
```

For more information about LMDeploy pipeline usage, please refer to [here](https://lmdeploy.readthedocs.io/en/latest/inference/pipeline.html).

### Serving

LMDeploy's `api_server` enables models to be easily packed into services with a single command. The provided RESTful APIs are compatible with OpenAI's interfaces. Below are an example of service startup:

```bash
lmdeploy serve api_server internlm/internlm3-8b-instruct --model-name internlm3-8b-instruct --server-port 23333
```

Then you can send a chat request to the server:

```bash
curl http://localhost:23333/v1/chat/completions \
    -H "Content-Type: application/json" \
    -d '{
    "model": "internlm3-8b-instruct",
    "messages": [
        {"role": "user", "content": "Please tell me five scenic spots in Shanghai"}
    ]
    }'
```

Find more details in the [LMDeploy documentation](https://lmdeploy.readthedocs.io/en/latest/)
