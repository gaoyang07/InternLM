# SGLang inference

## Installation

```bash
pip3 install "sglang[srt]>=0.4.1.post6" --find-links https://flashinfer.ai/whl/cu124/torch2.4/flashinfer/
```

## Inference with SGLang

You can launch an OpenAI compatible server with the following command:

```bash
python3 -m sglang.launch_server --model internlm/internlm3-8b-instruct --trust-remote-code --chat-template internlm2-chat
```

Then you can send a chat request to the server:

```python
import openai
client = openai.Client(
    base_url="http://127.0.0.1:30000/v1", api_key="EMPTY")

# Chat completion
response = client.chat.completions.create(
    model="default",
    messages=[
        {"role": "system", "content": "You are a helpful AI assistant"},
        {"role": "user", "content": "List 3 countries and their capitals."},
    ],
    temperature=0,
    max_tokens=64,
)
print(response)
```
