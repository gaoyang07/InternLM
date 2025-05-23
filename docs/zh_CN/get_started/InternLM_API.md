# InternLM API

使用 InternLM 的 API 接口进行调用。

## 基本调用

```python
# API 调用示例
import requests

response = requests.post("API_ENDPOINT", json={"prompt": "你好"})
print(response.json())
```
