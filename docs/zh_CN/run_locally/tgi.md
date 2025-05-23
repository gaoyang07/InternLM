# 使用 Text Generation Inference (TGI) 运行 InternLM

Text Generation Inference (TGI) 是 Hugging Face 开发的高性能文本生成推理服务器。

## 安装和运行

使用 Docker 运行 TGI：

```bash
docker run --gpus all --shm-size 1g -p 8080:80 -v $volume:/data ghcr.io/huggingface/text-generation-inference:latest --model-id InternLM/internlm3-8b-instruct
```

## API 调用

```bash
curl 127.0.0.1:8080/generate \
    -X POST \
    -d '{"inputs":"你好，请介绍一下深度学习","parameters":{"max_new_tokens":200}}' \
    -H 'Content-Type: application/json'
```

## 特性

- 高性能推理
- 动态批处理
- 量化支持
- OpenAPI 兼容接口
