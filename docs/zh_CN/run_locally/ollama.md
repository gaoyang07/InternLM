# 使用 Ollama 运行 InternLM

Ollama 是一个轻量级、可扩展的框架，用于在本地构建和运行大语言模型。

## 安装 Ollama

请根据官方文档安装 Ollama：https://ollama.com/

## 拉取 InternLM 模型

```bash
ollama pull internlm/internlm3-8b-instruct
```

## 运行模型

```bash
ollama run internlm/internlm3-8b-instruct
```

## 与模型对话

模型启动后，您可以直接在终端中与 InternLM 进行对话。

```
>>> 你好！你是谁？
我是InternLM，一个由上海人工智能实验室开发的大语言模型。我可以帮助回答问题、协助编程、创作文本等等。有什么我可以帮助您的吗？

>>> 请介绍一下机器学习
机器学习是人工智能的一个分支，它使计算机能够在不被明确编程的情况下学习和改进性能...
```

## API 访问

Ollama 也提供了 REST API，您可以通过 HTTP 请求与模型交互：

```bash
curl http://localhost:11434/api/generate -d '{
  "model": "internlm/internlm3-8b-instruct",
  "prompt": "解释什么是深度学习",
  "stream": false
}'
```
